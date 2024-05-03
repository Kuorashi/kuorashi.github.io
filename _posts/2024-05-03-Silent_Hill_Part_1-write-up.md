---
title: Silent_Hill_Part_1 - FR - French | EN - english
author: cotes
date: 2024-05-03 00:34:00 +0800
categories: [write-up, MidnightFlag Backslash]
tags: [MidnightFlag Backslash, write-up]
---
'EN - English' at the end of 'FR - French version'

<a href="https://github.com/Kuorashi/file_challenge_ctf/tree/main/MidnightFlag%20Backslash/Silent_Hill_Part_1.zip" class="download-button">Download the zip of this challenge</a>

# FR - French

## Vérification de la faille :
Vérification de la SSTI ; si le code est exécuté, le site affichera 49 :
![image](https://github.com/Kuorashi/kuorashi.github.io/assets/125281823/aad01d25-bd38-41ff-86c8-0cb4c2134dd2)

Le code s'étant bien exécuté, on peut poursuivre.

## Exploitation de la faille
En recherchant des *payloads* pour exploiter ce type de faille, on en trouve un parfait pour ce que l'on veut faire :
![image](https://github.com/Kuorashi/kuorashi.github.io/assets/125281823/3e612570-7687-4061-98e9-8eb0efc3322e)


On situe notre emplacement sur le serveur avec :
![image](https://github.com/Kuorashi/kuorashi.github.io/assets/125281823/843502d6-2757-499f-85d9-fd1def6e66ee)


On effectue un `ls` sur la racine pour trouver quelque chose d'intéressant :
![image](https://github.com/Kuorashi/kuorashi.github.io/assets/125281823/48f3ad7f-0a10-40dd-a8c5-928bd1425fc7)

Découverte du dossier `/lakeviewhotel_secrets`.

`ls` sur le dossier `/lakeviewhotel_secrets` :
découverte du fichier `flag.txt`.

Lecture du fichier `flag.txt` :
![image](https://github.com/Kuorashi/kuorashi.github.io/assets/125281823/597180e3-c79e-4cbc-ae94-cc54ee6f5995)


____________________________________________________________________________________________________________________________

# EN - English

## Vulnerability Verification:
Verification of SSTI; if the code executes, the site will display 49:
![image](https://github.com/Kuorashi/kuorashi.github.io/assets/125281823/aad01d25-bd38-41ff-86c8-0cb4c2134dd2)
As the code has executed correctly, we can proceed.

## Exploit of the Vulnerability
While searching for payloads to exploit this type of vulnerability, we find one perfect for our needs:
![image](https://github.com/Kuorashi/kuorashi.github.io/assets/125281823/3e612570-7687-4061-98e9-8eb0efc3322e)

We locate our position on the server with:
![image](https://github.com/Kuorashi/kuorashi.github.io/assets/125281823/843502d6-2757-499f-85d9-fd1def6e66ee)

We run `ls` on the root directory to find something interesting:
![image](https://github.com/Kuorashi/kuorashi.github.io/assets/125281823/48f3ad7f-0a10-40dd-a8c5-928bd1425fc7)
Discovery of the folder `lakeviewhotel_secrets`.

`ls` on the `lakeviewhotel_secrets` folder:
discovery of the file `flag.txt`.

Reading the file `flag.txt`:
![image](https://github.com/Kuorashi/kuorashi.github.io/assets/125281823/597180e3-c79e-4cbc-ae94-cc54ee6f5995)
