---
layout: htb_item
title: "Dog"
os: "Linux"
difficulty: "Easy"
type: "machines"
image: "/assets/images/htb/machines/dog.png"
description: "Dog is an easy-rated Linux machine that involves reading sensitive information through an exposed git repository and exposing credentials to get administrator access to `BackdropCMS`. The admin privileges allow an attacker to exploit Remote Code Execution by uploading a malicious archive containing a `PHP` backdoor to gain an initial foothold. The `johncusack` user account also reuses the `BackdropCMS` password. After compromising the `johncusack` account, the attacker finds that the user can run the `bee` executable with `sudo` privileges, which allows the attacker to gain root privileges."
date:   2025-10-23 10:10:37 +0200
---

![Dog pwned](/assets/images/htb/machines/dog_pwned.png)

# Description
Dog is an easy-rated Linux machine that involves reading sensitive information through an exposed git repository and exposing credentials to get administrator access to `BackdropCMS`. The admin privileges allow an attacker to exploit Remote Code Execution by uploading a malicious archive containing a `PHP` backdoor to gain an initial foothold. The `johncusack` user account also reuses the `BackdropCMS` password. After compromising the `johncusack` account, the attacker finds that the user can run the `bee` executable with `sudo` privileges, which allows the attacker to gain root privileges.
