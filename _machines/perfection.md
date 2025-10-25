---
layout: htb_item
title: "Perfection"
os: "Linux"
difficulty: "Easy"
type: "machines"
image: "/assets/images/htb/machines/perfection.png"
description: "Perfection is an easy Linux machine that features a web application with functionality to calculate student scores. This application is vulnerable to Server-Side Template Injection (SSTI) via regex filter bypass. A foothold can be gained by exploiting the SSTI vulnerability. Enumerating the user reveals they are part of the `sudo` group. Further enumeration uncovers a database with password hashes, and the user&amp;amp;#039;s mail reveals a possible password format. Using a mask attack on the hash, the user&amp;amp;#039;s password is obtained, which is leveraged to gain `root` access."
date:   2025-10-23 10:10:37 +0200
---

![Perfection pwned](/assets/images/htb/machines/perfection_pwned.png)

# Description
Perfection is an easy Linux machine that features a web application with functionality to calculate student scores. This application is vulnerable to Server-Side Template Injection (SSTI) via regex filter bypass. A foothold can be gained by exploiting the SSTI vulnerability. Enumerating the user reveals they are part of the `sudo` group. Further enumeration uncovers a database with password hashes, and the user&amp;amp;#039;s mail reveals a possible password format. Using a mask attack on the hash, the user&amp;amp;#039;s password is obtained, which is leveraged to gain `root` access.
