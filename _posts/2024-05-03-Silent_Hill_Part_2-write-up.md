---
title: Silent_Hill_Part_2 - FR - French | EN - english
author: cotes
date: 2024-05-03 16:17:00 +0800
categories: [write-up, MidnightFlag Backslash]
tags: [MidnightFlag Backslash, write-up]
---
'EN - English' at the end of 'FR - French version'

<a href="https://github.com/Kuorashi/file_challenge_ctf/tree/main/MidnightFlag%20Backslash/Silent_hill_part_2.png.zip" class="download-button">Download the zip of this challenge</a>

# FR - French

## découper en 4 l’image :
```bash
convert Silent_hill_2.png -crop 2x2@ +repage image_part%d.png
```
ont obtient 4 image : image_part0.png, image_part1.png, image_part2.png, image_part3.png

## image_part0.png : la cassette
soit via l’utilisation d’un script comme python en essayant d’extraire le premier bit faible, le
deuxième, le troisième… ou d’outil comme zsteg ont remarque que du code est caché dans les
3 derniers bits LSB sur le RGB dans l’ordre RGB.

Une fois le code extrait ont se rend compte que le code est en base 64.

via cyberchef en utilisant la fonction ‘from base 64’ plusieurs indicateurs sont présent pour
comprendre qu’il s’agit d’un fichier vidéo. A ce moment il ne reste plus qu’a utilisé un
convertisseur base64 vers vidéo par exemple pour voir une partie du flag.

## image_part1.png : le livre crimson (rouge)
soit via l’utilisation d’un script comme python en essayant d’extraire le premier bit faible, le
deuxième, le troisième… ou d’outil comme zsteg ont remarque que du code est caché dans les
3 derniers bits LSB sur le RGB dans l’ordre RGB.

Le texte récupéré est en clair ont peut voir un bout du flag

## image_part2.png : le livre lost memory (livre ouvert)
soit via l’utilisation d’un script comme python en essayant d’extraire le premier bit faible, le
deuxième, le troisième… ou d’outil comme zsteg ont remarque que du code est caché dans les
3 derniers bits LSB sur le RGB dans l’ordre RGB.

Une fois le code extrait ont se rend compte que le code est en base 64.

convertir le code base64 en texte. Ont peut voir un autre bout du flag.

## image_part3.png : la radio
convert Silent_hill_2.png -crop 2x2@ +repage image_part%d.png
soit via l’utilisation d’un script comme python en essayant d’extraire le premier bit faible, le
deuxième, le troisième… ou d’outil comme zsteg ont remarque que du code est caché dans les
3 derniers bits LSB sur le RGB dans l’ordre RGB.

Une fois le code extrait ont se rend compte que le code est en base 64.

via cyberchef en utilisant la fonction ‘from base 64’ plusieurs indicateurs sont présent pour
comprendre qu’il s’agit d’un fichier audio. A ce moment il ne reste plus qu’a utilisé un
convertisseur base64 vers audio par exemple pour entendre une partie
____________________________________________________________________________________________________________________________

# EN - English

## Split the image into 4:
```bash
convert Silent_hill_2.png -crop 2x2@ +repage image_part%d.png
```
This results in 4 images: image_part0.png, image_part1.png, image_part2.png, image_part3.png.

## image_part0.png: the tape
Using a script in Python to extract the least significant bit, the second, the third, etc., or using a tool like zsteg, it's observed that code is hidden within the last 3 LSBs of the RGB channels in RGB order.

Once the code is extracted, it's apparent that the code is in base64 format.

Using CyberChef with the ‘from base64’ function reveals several indicators that it's a video file. At this point, one could use a base64 to video converter to view a portion of the flag.

## image_part1.png: the crimson (red) book
Using a Python script or a tool like zsteg to extract bits, it's noticed that code is hidden within the last 3 LSBs of the RGB channels in RGB order.

The extracted text is in plain text revealing a part of the flag.

## image_part2.png: the lost memory (open book)
Using either a script or zsteg, code is observed hidden in the last 3 LSBs of the RGB channels in RGB order.

After extracting, it's clear that the code is in base64 format.

Convert the base64 code to text to see another part of the flag.

## image_part3.png: the radio
```bash
convert Silent_hill_2.png -crop 2x2@ +repage image_part%d.png
```
Using a script or zsteg, it's observed that code is hidden within the last 3 LSBs of the RGB channels in RGB order.

After extraction, the code is revealed to be in base64 format.

Using CyberChef with the ‘from base64’ function shows several indicators that it's an audio file. At this point, one might use a base64 to audio converter to hear a part of the flag.
