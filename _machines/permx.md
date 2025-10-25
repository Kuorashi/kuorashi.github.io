---
layout: htb_item
title: "PermX"
os: "Linux"
difficulty: "Easy"
type: "machines"
image: "/assets/images/htb/machines/permx.png"
description: "`PermX` is an Easy Difficulty Linux machine featuring a learning management system vulnerable to unrestricted file uploads via [CVE-2023-4220](https://nvd.nist.gov/vuln/detail/CVE-2023-4220). This vulnerability is leveraged to gain a foothold on the machine. Enumerating the machine reveals credentials that lead to SSH access. A `sudo` misconfiguration is then exploited to gain a `root` shell."
date:   2025-10-23 10:10:37 +0200
---

![PermX pwned](/assets/images/htb/machines/permx_pwned.png)

# Description
PermX is an Easy Difficulty Linux machine featuring a learning management system vulnerable to unrestricted file uploads via [CVE-2023-4220](https://nvd.nist.gov/vuln/detail/CVE-2023-4220). This vulnerability is leveraged to gain a foothold on the machine. Enumerating the machine reveals credentials that lead to SSH access. A `sudo` misconfiguration is then exploited to gain a `root` shell.
