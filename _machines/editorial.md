---
layout: htb_item
title: "Editorial"
os: "Linux"
difficulty: "Easy"
type: "machines"
image: "/assets/images/htb/machines/editorial.png"
description: "`Editorial` is an easy difficulty Linux machine that features a publishing web application vulnerable to `Server-Side Request Forgery (SSRF)`. This vulnerability is leveraged to gain access to an internal running API, which is then leveraged to obtain credentials that lead to `SSH` access to the machine. Enumerating the system further reveals a Git repository that is leveraged to reveal credentials for a new user. The `root` user can be obtained by exploiting [CVE-2022-24439](https://nvd.nist.gov/vuln/detail/CVE-2022-24439) and the sudo configuration."
date:   2025-10-23 10:10:37 +0200
---

![Editorial pwned](/assets/images/htb/machines/editorial_pwned.png)

# Description
`Editorial` is an easy difficulty Linux machine that features a publishing web application vulnerable to `Server-Side Request Forgery (SSRF)`. This vulnerability is leveraged to gain access to an internal running API, which is then leveraged to obtain credentials that lead to `SSH` access to the machine. Enumerating the system further reveals a Git repository that is leveraged to reveal credentials for a new user. The `root` user can be obtained by exploiting [CVE-2022-24439](https://nvd.nist.gov/vuln/detail/CVE-2022-24439) and the sudo configuration.