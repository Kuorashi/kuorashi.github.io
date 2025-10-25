---
layout: htb_item
title: "IClean"
os: "Linux"
difficulty: "Medium"
type: "machines"
image: "/assets/images/htb/machines/iclean.png"
description: "IClean is a medium-difficulty Linux machine featuring a website for a cleaning services company. The website contains a form where users can request a quote, which is found to be vulnerable to Cross-Site Scripting (XSS). This vulnerability is exploited to steal an admin cookie, which is then used to access the administrator dashboard. The page is vulnerable to Server-Side Template Injection (SSTI), allowing us to obtain a reverse shell on the box. Enumeration reveals database credentials, which are leveraged to gain access to the database, leading to the discovery of a user hash. Cracking this hash provides `SSH` access to the machine. The user’s mail mentions working with PDFs. By examining the `sudo` configuration, it is found that the user can run `qpdf` as `root`. This is leveraged to attach the `root` private key to a PDF, which is then used to gain privileged access to the machine."
date:   2025-10-23 10:10:37 +0200
---

![IClean pwned](/assets/images/htb/machines/iclean_pwned.png)

# Description
IClean is a medium-difficulty Linux machine featuring a website for a cleaning services company. The website contains a form where users can request a quote, which is found to be vulnerable to Cross-Site Scripting (XSS). This vulnerability is exploited to steal an admin cookie, which is then used to access the administrator dashboard. The page is vulnerable to Server-Side Template Injection (SSTI), allowing us to obtain a reverse shell on the box. Enumeration reveals database credentials, which are leveraged to gain access to the database, leading to the discovery of a user hash. Cracking this hash provides `SSH` access to the machine. The user’s mail mentions working with PDFs. By examining the `sudo` configuration, it is found that the user can run `qpdf` as `root`. This is leveraged to attach the `root` private key to a PDF, which is then used to gain privileged access to the machine.