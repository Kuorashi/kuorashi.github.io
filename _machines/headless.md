---
layout: htb_item
title: "Headless"
os: "Linux"
difficulty: "Easy"
type: "machines"
image: "/assets/images/htb/machines/headless.png"
description: "Headless is an easy-difficulty Linux machine that features a `Python Werkzeug` server hosting a website. The website has a customer support form, which is found to be vulnerable to blind Cross-Site Scripting (XSS) via the `User-Agent` header. This vulnerability is leveraged to steal an admin cookie, which is then used to access the administrator dashboard. The page is vulnerable to command injection, leading to a reverse shell on the box. Enumerating the user’s mail reveals a script that does not use absolute paths, which is leveraged to get a shell as root."
date:   2025-10-23 10:10:37 +0200
---

![Headless pwned](/assets/images/htb/machines/headless_pwned.png)

# Description
Headless is an easy-difficulty Linux machine that features a `Python Werkzeug` server hosting a website. The website has a customer support form, which is found to be vulnerable to blind Cross-Site Scripting (XSS) via the `User-Agent` header. This vulnerability is leveraged to steal an admin cookie, which is then used to access the administrator dashboard. The page is vulnerable to command injection, leading to a reverse shell on the box. Enumerating the user’s mail reveals a script that does not use absolute paths, which is leveraged to get a shell as root.