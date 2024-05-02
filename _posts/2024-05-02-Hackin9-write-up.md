---
title: Hackin9 - FR - French | EN - english
author: cotes
date: 2024-05-02 00:34:00 +0800
categories: [write-up, MidnightFlag Backslash]
tags: [MidnightFlag Backslash, write-up]
---
'EN - English' at the end of 'FR - French version'

<a href="https://github.com/Kuorashi/file_challenge_ctf/tree/main/MidnightFlag%20Backslash/hackin9.jpg.zip" class="download-button">Download the zip of this challenge</a>

# FR - French

Les majuscules et les minuscules sont mal utilisées. L'enchaînement pourrait faire penser à un code binaire où les majuscules sont des 1 et les minuscules des 0.

Convertir le texte en binaire, les majuscules étant des 1 et les minuscules des 0. Une fois fait, on obtient le code :

```binary
01001101010000110101010001000110011110110100001001101001001100110110111001011111010
01010001100000111010100110011011100100101111101101010011001010101111101100011011011
11011011010110001001101100011001010101111101110000011011110111010101110010010111110
110000101110110011011110110100101111101
```

On convertit le binaire en texte, on obtient :
`MCTF{Bi3n_J0u3r_je_comble_pour_avoi}`

PS : Le flag semble incomplet, c'est normal, c'était pour avoir la même longueur de texte que de binaire, j'avais la flemme.

____________________________________________________________________________________________________________________________

# EN - English

Capitalization is used incorrectly. The sequence might suggest a binary code where uppercase letters are '1' and lowercase letters are '0'.

Convert the text to binary, with uppercase as '1' and lowercase as '0'. Once converted, we obtain the code:
```binary
01001101010000110101010001000110011110110100001001101001001100110110111001011111010
01010001100000111010100110011011100100101111101101010011001010101111101100011011011
11011011010110001001101100011001010101111101110000011011110111010101110010010111110
110000101110110011011110110100101111101
```

When we convert the binary to text, we get:
```
MCTF{Bi3n_J0u3r_je_comble_pour_avoi}
```

PS: The flag seems incomplete; this is intentional to maintain the same length of text as the binary. I was too lazy to complete it.
