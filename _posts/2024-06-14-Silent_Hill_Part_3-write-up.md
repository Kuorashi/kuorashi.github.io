---
title: Silent_Hill_Part_3 - FR - French | EN - english
author: kuorashi
date: 2024-06-14 00:34:00 +0800
categories: [write-up, MidnightFlag Backslash]
tags: [MidnightFlag Backslash, write-up]
---
'EN - English' at the end of 'FR - French version'

<a href="https://github.com/Kuorashi/file_challenge_ctf/releases/download/FileMe!/snake.zip" class="download-button">Download the zip of this challenge</a>

# FR - French

**Étape 1 : Décodage du code Python**

Le code Python est chiffré en utilisant l'alphabet phonétique OTAN. Nous devons d'abord le déchiffrer en le convertissant en texte clair.
Pour comprendre l'utilité du script Python, nous analysons le code qui cache et extrait des données dans une image en utilisant une méthode de stéganographie basée sur le dernier bit de poids faible du canal bleu des pixels.

**Code pour extraire le texte caché dans l'image :**

```python
from PIL import Image
import codecs

def rot13(text):
    return codecs.encode(text, 'rot_13')

png = Image.open("stegano.png")
pixels = list(png.getdata())

texte_bin = ""
for r, g, b in pixels:
    texte_bin += str(b & 1)

texte = ""
i = 0
while i < len(texte_bin) - 8:
    byte = texte_bin[i:i+8]
    if byte == '00000000':
        break
    texte += chr(int(byte, 2))
    i += 8

texte_clair = rot13(texte)

print("Texte récupéré et décodé :", texte_clair)
```

Ce code extrait les bits du canal bleu des pixels pour reconstituer un texte binaire, qu'il décode ensuite en texte clair après avoir appliqué un ROT13.

**Étape 2 : Extraction du texte caché**

En exécutant le script ci-dessus sur l'image `stegano.png`, nous récupérons le texte chiffré.

**Étape 3 : Récupération du flag chiffré**

Le texte extrait contient le flag encodé `EKEJ{Ja3y3_4z3_j0f_W4vW}`.

**Étape 4 : Conversion du code hexadécimal en image**

Nous trouvons la clé de Vigenère cachée en hexadécimal dans un fichier texte `s3cUr3_Tr4nsf3rt.txt`. Cette clé est obtenue en convertissant une image en hexadécimal, puis en décryptant le texte en utilisant un éditeur graphique pour révéler la clé écrite.

**Étape 5 : Récupération de la clé**

En utilisant un éditeur comme Paint 3D, nous découvrons la clé `SILENTHILLKEYFORLATER`.

**Étape 6 : Déchiffrement du flag**

En déduisant que le chiffrement utilisé est Vigenère, nous utilisons la clé récupérée pour déchiffrer le flag chiffré.

**Code pour déchiffrer le flag :**

```python
def vigenere_decrypt(ciphertext, key):
    plaintext = ""
    key_length = len(key)
    key_as_int = [ord(i) for i in key]
    ciphertext_int = [ord(i) for i in ciphertext]
    for i in range(len(ciphertext_int)):
        value = (ciphertext_int[i] - key_as_int[i % key_length]) % 26
        plaintext += chr(value + 65)
    return plaintext

ciphertext = "EKEJ{Ja3y3_4z3_j0f_W4vW}"
key = "SILENTHILLKEYFORLATER"
plaintext = vigenere_decrypt(ciphertext, key)

print("Flag déchiffré :", plaintext)
```

En exécutant ce code, nous obtenons le flag déchiffré `MCTF{Wh3r3_4r3_y0u_M4rY}`.

**Étape 7 : Validation du challenge**

Avec le flag déchiffré en main, le challenge est complété et validé.

---

# EN - English

**Step 1: Decoding the Python Code**

The Python code is encrypted using the NATO phonetic alphabet. We first need to decrypt it to convert it to plain text.
To understand the utility of the Python script, we analyze the code that hides and extracts data in an image using a steganography method based on the least significant bit of the blue channel of pixels.

**Code to extract hidden text from the image:**

```python
from PIL import Image
import codecs

def rot13(text):
    return codecs.encode(text, 'rot_13')

png = Image.open("stegano.png")
pixels = list(png.getdata())

texte_bin = ""
for r, g, b in pixels:
    texte_bin += str(b & 1)

texte = ""
i = 0
while i < len(texte_bin) - 8:
    byte = texte_bin[i:i+8]
    if byte == '00000000':
        break
    texte += chr(int(byte, 2))
    i += 8

texte_clair = rot13(texte)

print("Retrieved and decoded text:", texte_clair)
```

This code extracts the bits from the blue channel of the pixels to reconstruct a binary text, which it then decodes into plain text after applying a ROT13.

**Step 2: Extracting the Hidden Text**

By running the above script on the image `stegano.png`, we retrieve the encrypted text.

**Step 3: Retrieving the Encrypted Flag**

The extracted text contains the encoded flag `EKEJ{Ja3y3_4z3_j0f_W4vW}`.

**Step 4: Converting the Hexadecimal Code into an Image**

We find the Vigenère key hidden in hexadecimal in a text file `s3cUr3_Tr4nsf3rt.txt`. This key is obtained by converting an image to hexadecimal, then decrypting the text using a graphical editor to reveal the written key.

**Step 5: Retrieving the Key**

Using an editor like Paint 3D, we discover the key `SILENTHILLKEYFORLATER`.

**Step 6: Decrypting the Flag**

Deducing that the encryption used is Vigenère, we use the retrieved key to decrypt the encoded flag.

**Code to decrypt the flag:**

```python
def vigenere_decrypt(ciphertext, key):
    plaintext = ""
    key_length = len(key)
    key_as_int = [ord(i) for i in key]
    ciphertext_int = [ord(i) for i in ciphertext]
    for i in range(len(ciphertext_int)):
        value = (ciphertext_int[i] - key_as_int[i % key_length]) % 26
        plaintext += chr(value + 65)
    return plaintext

ciphertext = "EKEJ{Ja3y3_4z3_j0f_W4vW}"
key = "SILENTHILLKEYFORLATER"
plaintext = vigenere_decrypt(ciphertext, key)

print("Decrypted flag:", plaintext)
```

By running this code, we obtain the decrypted flag `MCTF{Wh3r3_4r3_y0u_M4rY}`.

**Step 7: Validating the Challenge**

With the decrypted flag in hand, the challenge is completed and validated.

