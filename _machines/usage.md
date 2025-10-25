---
layout: htb_item
title: "Usage"
os: "Linux"
difficulty: "Easy"
type: "machines"
image: "/assets/images/htb/machines/usage.png"
description: "Usage is an easy Linux machine that features a blog site vulnerable to SQL injection, which allows the administrator&amp;amp;#039;s hashed password to be dumped and cracked. This leads to access to the admin panel, where an outdated `Laravel` module is abused to upload a PHP web shell and obtain remote code execution. On the machine, plaintext credentials stored in a file allow SSH access as another user, who can run a custom binary as `root`. The tool makes an insecure call to `7zip`, which is leveraged to read the `root` user&amp;amp;#039;s private SSH key and fully compromise the system. "
date:   2025-10-23 10:10:37 +0200
---

![Usage pwned](/assets/images/htb/machines/usage_pwned.png)

# Description
Usage is an easy Linux machine that features a blog site vulnerable to SQL injection, which allows the administrator&amp;amp;#039;s hashed password to be dumped and cracked. This leads to access to the admin panel, where an outdated `Laravel` module is abused to upload a PHP web shell and obtain remote code execution. On the machine, plaintext credentials stored in a file allow SSH access as another user, who can run a custom binary as `root`. The tool makes an insecure call to `7zip`, which is leveraged to read the `root` user&amp;amp;#039;s private SSH key and fully compromise the system. 
