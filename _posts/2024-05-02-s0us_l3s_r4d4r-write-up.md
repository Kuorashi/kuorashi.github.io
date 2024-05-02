---
title: s0us_l3s_r4d4r - FR - French | EN - english
author: cotes
date: 2024-05-02 00:34:00 +0800
categories: [write-up, MidnightFlag Backslash]
tags: [MidnightFlag Backslash, write-up]
---
'EN - English' at the end of 'FR - French version'

<a href="https://github.com/Kuorashi/file_challenge_ctf/tree/main/MidnightFlag%20Backslash/Gorrille_wallpaper.zip" class="download-button">Download the zip of this challenge</a>

# FR - French

## trouver le début du code python :

chercher dans les strings de l'image :
```bash
strings Gorille_Wallpaper.jpg
```

Version rapide :
```bash
strings Gorille_Wallpaper.jpg | grep import
```

## trouver tout le code python

ont modifie un peu la commande grep pour afficher sur une plage de -20lignes à +20lignes

```bash
strings Gorille_Wallpaper_pasobf.jpg | grep -B 20 -A 20 "import"
```

Ont peut voir le code python suivant :
```python
import string; alph = string.ascii_letters;flag_enc = "109 115 104 110 { 130 111 131 104 111 132 108 122 123 145 104 122 149 121 118 119 149 118 123 }"
def decode_flag(flag):
    lst = flag.split(" ")
    new_flag = ""
    for item in lst:
        if item != '{' and item != '}':
            new_flag += alph[int(item) % 25]
        else:
            new_flag += item
    print(new_flag)
def encode_flag(flag):
    text = ""
    for i in flag:
        if i not in alph:
            text += i + " "
        else:
            text += f"{alph.index(i) + int(flag_enc.split(' ')[2])} + "
    print(text)
decode_flag(flag_enc)
```
## Réparer le code python

L'alphabet `string.ascii_letters` contient 52 caractères (26 majuscules et 26 minuscules), donc il faut ajuster les modulo pour éviter les erreurs d'index.

```python
import string; alph = string.ascii_letters;flag_enc = "109 115 104 110 { 130 111 131 104 111 132 108 122 123 145 104 122 149 121 118 119 149 118 123 }"
def decode_flag(flag):
    lst = flag.split(" ")
    new_flag = ""
    for item in lst:
        if item != '{' and item != '}':
            new_flag += alph[int(item) % 52]
        else:
            new_flag += item
    print(new_flag)
def encode_flag(flag):
    text = ""
    for i in flag:
        if i not in alph:
            text += i + " "
        else:
            text += f"{alph.index(i) + int(flag_enc.split(' ')[2])} + "
    print(text)
decode_flag(flag_enc)
```

## lancer le script python

ont récupère flag{AhBahCestPasTropTot}, ont le remet au format de flag du Midnight : MCTF{flag{AhBahCestPasTropTot}}

____________________________________________________________________________________________________________________________

# EN - English

## Finding the start of the Python code:

Search in the strings of the image:
```
strings Gorille_Wallpaper.jpg
```

Quick version:
```
strings Gorille_Wallpaper.jpg | grep import
```

## Finding all the Python code

We slightly modify the grep command to display a range of -20 lines to +20 lines

```
strings Gorille_Wallpaper_pasobf.jpg | grep -B 20 -A 20 "import"
```

We can see the following Python code:
```python
import string; alph = string.ascii_letters; flag_enc = "109 115 104 110 { 130 111 131 104 111 132 108 122 123 145 104 122 149 121 118 119 149 118 123 }"
def decode_flag(flag):
    lst = flag.split(" ")
    new_flag = ""
    for item in lst:
        if item != '{' and item != '}':
            new_flag += alph[int(item) % 25]
        else:
            new_flag += item
    print(new_flag)
def encode_flag(flag):
    text = ""
    for i in flag:
        if i not in alph:
            text += i + " "
        else:
            text += f"{alph.index(i) + int(flag_enc.split(' ')[2])} + "
    print(text)
decode_flag(flag_enc)
```
## Repairing the Python code

The `string.ascii_letters` contains 52 characters (26 uppercase and 26 lowercase), so the modulo should be adjusted to avoid index errors.

```python
import string; alph = string.ascii_letters; flag_enc = "109 115 104 110 { 130 111 131 104 111 132 108 122 123 145 104 122 149 121 118 119 149 118 123 }"
def decode_flag(flag):
    lst = flag.split(" ")
    new_flag = ""
    for item in lst:
        if item != '{' and item != '}':
            new_flag += alph[int(item) % 52]
        else:
            new_flag += item
    print(new_flag)
def encode_flag(flag):
    text = ""
    for i in flag:
        if i not in alph:
            text += i + " "
        else:
            text += f"{alph.index(i) + int(flag_enc.split(' ')[2])} + "
    print(text)
decode_flag(flag_enc)
```

## Running the Python script

We retrieve the flag{AhBahCestPasTropTot}, and reformat it to the Midnight format: MCTF{flag{AhBahCestPasTropTot}}
