---
layout: post
title: "Evill-SSP : Comprendre les Security Support Providers comme vecteur d'attaque"
date: 2025-10-25
categories: [red-team, windows]
tags: [ssp, credentials, windows-internals, offensive-security]
image: "/assets/images/projects/evilssp.png"
excerpt: "Dans le cadre de mes recherches en sécurité offensive, j'ai développé **Evill-SSP**, un projet de recherche visant à démontrer comment les Security Support Providers (SSP) de Windows peuvent ...."
---

<!--more-->

## Introduction

Dans le cadre de mes recherches en sécurité offensive, j'ai développé **Evill-SSP**, un projet de recherche visant à démontrer comment les Security Support Providers (SSP) de Windows peuvent être détournés pour intercepter des identifiants système. Cet article présente le fonctionnement technique des SSP, leur exploitation potentielle, et les mécanismes de défense associés.

⚠️ **Avertissement** : Ce projet est strictement à but éducatif et de recherche. Le code complet n'est volontairement pas fourni pour éviter tout usage malveillant. Toute utilisation sur un système sans autorisation explicite constitue une infraction pénale.

**Projet GitHub** : [Kuorashi/Evill-SSP](https://github.com/Kuorashi/Evill-SSP)

## Partie 1 : Les Security Support Providers (SSP)

### Qu'est-ce qu'un SSP ?

Les Security Support Providers (SSP) sont l'implémentation de l'interface SSPI (Security Support Provider Interface) qui permet aux applications Windows d'effectuer des opérations d'authentification de manière standardisée. Un SSP est contenu dans une bibliothèque dynamique (DLL) qui implémente SSPI en rendant disponibles un ou plusieurs packages de sécurité aux applications.

### Architecture et fonctionnement

Les SSP par défaut qui invoquent des protocoles d'authentification spécifiques dans Windows sont incorporés dans SSPI sous forme de DLL. Ces SSP fonctionnent au sein du processus **LSASS** (Local Security Authority Subsystem Service), le composant Windows responsable de l'application des politiques de sécurité système.

**SSP natifs de Windows** :
- **Kerberos** : Protocole standard de l'industrie utilisé avec un mot de passe ou une carte à puce pour une connexion interactive, et protocole d'authentification préféré pour les services Windows
- **NTLM** : Protocole de messagerie binaire utilisé par SSPI pour permettre l'authentification par défi-réponse NTLM
- **Negotiate** : Sélection automatique entre Kerberos et NTLM
- **Digest** : Authentification HTTP
- **Schannel** : Protocoles SSL/TLS
- **CredSSP** : Credential Security Support Provider

### Le mécanisme d'enregistrement

Les SSP sont enregistrés via deux clés de registre : HKLM\SYSTEM\CurrentControlSet\Control\Lsa\Security Packages et HKLM\SYSTEM\CurrentControlSet\Control\Lsa\OSConfig\Security Packages. Lorsqu'un nouveau SSP est ajouté à cette liste, LSASS le charge automatiquement au prochain redémarrage, ou peut être chargé dynamiquement avec l'API Windows AddSecurityPackage.

## Partie 2 : Les SSP comme vecteur d'attaque

### Contexte historique

L'exploitation des SSP comme vecteur d'attaque a été popularisée par des outils de recherche en sécurité. Mimikatz, développé par Benjamin Delpy en 2007, comprend deux composants optionnels : mimidrv (un pilote pour interagir avec le noyau Windows) et mimilib (qui fournit des fonctionnalités incluant le contournement d'AppLocker, les packages d'authentification/SSP, les filtres de mots de passe). Mimilib fonctionne en tirant parti du fait qu'un Security Support Provider reçoit des identifiants en clair via l'interface SSP, ce qui signifie que les identifiants peuvent être exfiltrés en clair.

### Pourquoi les SSP sont-ils attractifs pour les attaquants ?

Une fois chargées dans la LSA, les DLL SSP ont accès aux mots de passe chiffrés et en clair stockés dans Windows, tels que le mot de passe de domaine de tout utilisateur connecté ou les codes PIN de cartes à puce.

**Avantages pour un attaquant** :
1. **Position privilégiée** : Exécution dans le contexte de LSASS avec les privilèges SYSTEM
2. **Accès direct aux credentials** : Interception en clair avant chiffrement
3. **Persistance** : Chargement automatique à chaque démarrage
4. **Discrétion** : Difficile à détecter sans solutions EDR avancées
5. **Légitimité apparente** : Les SSP sont des composants système normaux

### Classification MITRE ATT&CK

Cette technique est référencée dans le framework MITRE ATT&CK sous l'identifiant T1547.005 - Boot or Logon Autostart Execution: Security Support Provider.

## Partie 3 : Writeup technique - Evill-SSP

### Architecture du projet

Evill-SSP démontre les concepts de base d'un SSP malveillant. Le projet est composé de :

**Composants principaux** :
- `evildll.cpp` : Code source de la DLL SSP (incomplet volontairement)
- `srv-creds-http.py` : Serveur d'écoute HTTP (Flask)
- `srv-creds-https.py` : Serveur d'écoute HTTPS (Flask)
- `dlltoexe.ps1` : Script PowerShell conceptuel pour le déploiement

### Implémentation d'un SSP custom

Un SSP doit implémenter l'interface SSPI avec plusieurs fonctions obligatoires. Les fonctions essentielles incluent :

- `SpLsaModeInitialize()` : Initialisation du provider lors du chargement dans LSASS
- `SpAcceptCredentials()` : Fonction critique appelée par LSASS à chaque authentification réussie
- `SpShutdown()` : Nettoyage lors de l'arrêt

La fonction `SpAcceptCredentials()` est le point d'interception où les credentials (nom d'utilisateur, domaine, mot de passe) sont disponibles.

### Configuration de compilation

D'après le README du projet, la compilation nécessite :

**Configuration Visual Studio** :
- Type de projet : Dynamic Link Library (DLL)
- Nom du projet : `evildll`
- Remplacer `dllmain.cpp` par le contenu de `evildll.cpp`
- Modifier la ligne 55 pour ajouter l'IP du serveur de destination et le port
- Configuration : Release x64
- C/C++ > Général > Répertoires Include : Ajouter le chemin du Windows SDK
- C/C++ > En-têtes précompilés : Ne pas utiliser

### Serveur d'exfiltration

Le concept repose sur l'exfiltration HTTP/HTTPS des credentials interceptés. Les serveurs Flask exposent deux endpoints :

**Endpoints API** :
- `/receive_credentials` (POST) : Réception des credentials interceptés
- `/health` (GET) : Vérification de l'état du serveur

**Lancement des serveurs** :
```bash
# Serveur HTTP
python3 srv-creds-http.py

# Serveur HTTPS (nécessite certificats)
python3 srv-creds-https.py --cert cert.pem --key key.pem
```

**Génération des certificats SSL/TLS** :
```bash
openssl genrsa -out key.pem 2048
openssl req -new -key key.pem -out csr.pem
openssl x509 -req -days 365 -in csr.pem -signkey key.pem -out cert.pem
```

### Vecteur de déploiement

Le script PowerShell conceptuel `dlltoexe.ps1` démontre le processus :

1. Lancement d'un exécutable légitime (ex: Firefox) pour masquer l'activité
2. Copie de la DLL vers `C:\Windows\System32`
3. Modification de la clé de registre `HKLM\SYSTEM\CurrentControlSet\Control\Lsa\Security Packages`

**Extrait conceptuel du script** :
```powershell
# Modifier les chemins source/target de l'exe et de la dll
Start-Process "C:\chemin\vers\mon_programme.exe"
Copy-Item "C:\chemin\vers\evildll.dll" -Destination "C:\Windows\System32"
```

**Création d'un binaire autonome** :
```powershell
Install-Module -Name PS2EXE
Import-Module ps2exe
Invoke-PS2EXE .\dlltoexe.ps1 .\build_firefox.exe
```

### Défis techniques

**Privilèges requis** :
- Accès SYSTEM ou Administrateur nécessaire
- Modification de clés de registre protégées
- Écriture dans `System32`

**Contraintes de sécurité modernes** :
- Signature de code (Driver Signature Enforcement)
- Protection ELAM (Early Launch Anti-Malware)
- LSA Protection Mode (RunAsPPL)
- Credential Guard

## Partie 4 : Détection et défense

### Méthodes de détection

**1. Monitoring du registre** :
Les adversaires peuvent modifier les clés de registre HKLM\SYSTEM\CurrentControlSet\Control\Lsa\Security Packages pour ajouter de nouveaux SSP qui seront chargés au prochain démarrage du système. Toute modification doit être alertée et investiguée.

**2. Analyse de LSASS** :
- Monitoring des DLL chargées dans le processus LSASS
- Détection de DLL non signées ou provenant de chemins anormaux
- Retour d'une liste des providers enregistrés via EnumerateSecurityPackages pour révéler les SSP non autorisés

**3. Détection réseau** :
- Trafic HTTP/HTTPS inhabituel depuis LSASS
- Exfiltration de données sensibles
- Connexions vers des serveurs externes suspects

**4. Solutions EDR** :
Les solutions modernes détectent :
- Modifications de la clé LSA
- Injection de DLL dans LSASS
- Comportements anormaux de LSASS

### Mesures de mitigation

#### LSA Protection Mode

Credential Guard utilise la sécurité basée sur la virtualisation (VBS) pour isoler les secrets de sorte que seuls les logiciels système privilégiés puissent y accéder.

**Activation de LSA Protection** :
```powershell
New-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Control\Lsa" `
                 -Name "RunAsPPL" `
                 -Value 1 `
                 -PropertyType DWORD
```

#### Credential Guard

Avec Credential Guard activé, le processus LSA du système d'exploitation communique avec un composant appelé processus LSA isolé qui stocke et protège ces secrets (LSAIso.exe). Les données stockées par le processus LSA isolé sont protégées à l'aide de VBS et ne sont pas accessibles au reste du système d'exploitation.

Credential Guard prévient les attaques de vol d'identifiants en protégeant les hachages de mots de passe NTLM, les Ticket Granting Tickets (TGT) Kerberos et les identifiants stockés par les applications en tant qu'identifiants de domaine.

**Vérification de l'activation** :
```powershell
# Afficher les informations système pour confirmer Credential Guard
Get-ComputerInfo | Select-Object DeviceGuardSecurityServicesConfigured
```

**Configuration via Group Policy** :
- Computer Configuration > Administrative Templates > System > Device Guard
- Activer "Turn On Virtualization Based Security"
- Définir "Credential Guard Configuration" sur "Enabled with UEFI lock" ou "Enabled without lock"

#### Limitations de Credential Guard

Credential Guard ne protège pas la base de données Active Directory fonctionnant sur les contrôleurs de domaine Windows Server. Il ne protège pas non plus les pipelines d'entrée d'identifiants, tels que Windows Server exécutant la passerelle de bureau à distance.

Les identifiants fournis pour l'authentification NTLM ne sont pas protégés. Si un utilisateur est invité à entrer des identifiants pour l'authentification NTLM, ces identifiants sont vulnérables à la lecture depuis la mémoire LSASS.

#### Hardening supplémentaire

**Contrôle d'application** :
- AppLocker : Contrôle des DLL autorisées
- Windows Defender Application Control (WDAC) : Contrôle d'intégrité du code

**Stratégies d'authentification** :
- Limitation des comptes avec privilèges locaux
- Politique de mots de passe forte
- MFA (Multi-Factor Authentication) obligatoire
- Segmentation réseau (zero-trust)

### Indicateurs de compromission (IOC)

**Registre** :
- Clé `Security Packages` modifiée récemment
- Présence de DLL inconnues dans la liste des packages
- Horodatage suspect des modifications

**Système de fichiers** :
- DLL suspectes dans `System32` sans signature valide
- Timestamps de fichiers incohérents
- DLL avec des noms inhabituels ou aléatoires

**Réseau** :
- Connexions HTTP/HTTPS depuis `lsass.exe`
- Exfiltration de petits paquets réguliers
- Connexions vers des IPs externes non autorisées

**Processus** :
- DLL non-Microsoft chargées dans LSASS
- Handles anormaux vers des sockets réseau
- Utilisation mémoire inhabituelle de LSASS

## Partie 5 : Implications et réflexions

### Perspective Red Team

Les SSP malveillants représentent une technique de post-exploitation puissante pour :
- **Persistence** : Survie aux redémarrages système
- **Credential harvesting** : Collection passive et continue des identifiants
- **Lateral movement** : Utilisation des credentials collectés pour se déplacer latéralement

### Perspective Blue Team

La détection précoce est cruciale :
- Monitoring proactif de LSASS et des modifications de registre
- Baseline des Security Packages légitimes dans l'environnement
- Corrélation d'événements (registre + réseau + processus)
- Threat hunting régulier ciblant les techniques SSP
- Formation continue sur les nouvelles techniques d'attaque

### Évolution du paysage de sécurité

Microsoft renforce continuellement la sécurité de LSASS avec :
- Les appareils exécutant Windows Server 2025 ou version ultérieure ont Credential Guard activé par défaut s'ils répondent aux exigences matérielles
- Windows Defender System Guard
- Secured-core PC
- Protection matérielle (TPM 2.0, Microsoft Pluton)

## Conclusion

**Evill-SSP** démontre la criticité de la sécurisation de l'architecture d'authentification Windows. Bien que les SSP malveillants soient un vecteur d'attaque redoutable, les défenses modernes rendent leur exploitation de plus en plus difficile en environnement durci.

**Leçons principales** :
1. LSASS est une cible de choix nécessitant une protection maximale
2. Le monitoring du registre et des processus critiques est essentiel
3. Les solutions de virtualisation (Credential Guard) sont très efficaces
4. La défense en profondeur reste la meilleure stratégie
5. L'éducation et la sensibilisation sont cruciales

### Ressources et références

**Documentation du projet** :
- [GitHub - Kuorashi/Evill-SSP](https://github.com/Kuorashi/Evill-SSP) (code incomplet, à but éducatif uniquement)

**Documentation Microsoft** :
- [Security Support Provider Interface (SSPI)](https://learn.microsoft.com/en-us/windows/win32/rpc/security-support-provider-interface-sspi-)
- [Security Support Provider Interface Architecture](https://learn.microsoft.com/en-us/windows-server/security/windows-authentication/security-support-provider-interface-architecture)
- [Credential Guard Overview](https://learn.microsoft.com/en-us/windows/security/identity-protection/credential-guard/)
- [How Credential Guard Works](https://learn.microsoft.com/en-us/windows/security/identity-protection/credential-guard/how-it-works)
- [Configure Credential Guard](https://learn.microsoft.com/en-us/windows/security/identity-protection/credential-guard/configure)

**Frameworks de sécurité** :
- [MITRE ATT&CK - T1547.005: Security Support Provider](https://attack.mitre.org/techniques/T1547/005/)

**Recherche en sécurité** :
- [Exploring Mimikatz - Part 2 - SSP (XPN InfoSec Blog)](https://blog.xpnsec.com/exploring-mimikatz-part-2/)
- [Mimikatz - ADSecurity.org](https://adsecurity.org/?page_id=1821)

---

**Note finale** : Ce projet de recherche a été développé dans un environnement de laboratoire isolé strictement à des fins éducatives. Le code source complet n'est volontairement pas publié pour des raisons évidentes de sécurité. L'utilisation de ces techniques sur des systèmes sans autorisation explicite est illégale.

Si vous êtes un professionnel de la cybersécurité intéressé par la recherche collaborative ou si vous avez des questions sur les mécanismes de défense, n'hésitez pas à me contacter.

*Tags: #RedTeam #WindowsInternals #OffensiveSecurity #SSP #LSASS #ThreatResearch #Cybersecurity #CredentialGuard*