---
title: r3tro_auct1on - FR - French | EN - english
author: kuorashi
date: 2024-06-14 00:34:00 +0800
categories: [write-up, MidnightFlag Backslash]
tags: [MidnightFlag Backslash, write-up]
---
'EN - English' at the end of 'FR - French version'

<a href="https://github.com/Kuorashi/file_challenge_ctf/releases/download/FileMe!/snake.zip" class="download-button">Download the zip of this challenge</a>

# FR - French
AOI ne concerne pas les images de manga mais l'« Instantiation d'Objets Arbitraires ».
Avec un peu de recherche sur Internet, nous pouvons trouver un schéma à exploiter.
L'application crée une instance d'une classe basée sur des entrées utilisateur via $_GET['a'] et
transmet $_GET['b'] .
Nous pouvons utiliser la classe 'FileReader' pour lire des fichiers sur le serveur. $_GET['a'] pour
définir la classe $_GET['b'] pour choisir le fichier à lire Le bon payload est « ?
a=FileReader&b=/flag.txt ».
Le payload final ressemblerait à « http://webserver/index.php?a=FileReader&b=/flag.txt ».

---

# EN - English
AOI is not for manga pictures but for 'Arbitrary Object Instantiation.'
With a little research on the internet, we can find a pattern to exploit it.
The application creates an instance of a class based on user input through $_GET['a'] and
passes $_GET['b'] .
We can use the 'FileReader' class to read files on the server. $_GET['a'] to set the class
$_GET['b'] to choose the file to read The correct payload is "?a=FileReader&b=/flag.txt".
The final payload would look like "http://webserver/index.php?a=FileReader&b=/flag.txt"
