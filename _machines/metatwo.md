---
layout: htb_item
title: "MetaTwo"
os: "Linux"
difficulty: "Easy"
type: "machines"
image: "/assets/images/htb/machines/metatwo.png"
description: "MetaTwo is an easy Linux machine that features a website running Wordpress, which is using a plugin vulnerable to unauthenticated SQL injection ([CVE-2022-0739](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-0739)). It can be exploited to reveal the password hash of the Wordpress users which can be cracked to obtain the password for the Wordpress user `manager`. The Wordpress version in use is vulnerable to an XXE Vulnerability in the Media Library ([CVE-2021-29447](https://blog.wpsec.com/wordpress-xxe-in-media-library-cve-2021-29447/)), which can be exploited to obtain credentials for the FTP server. A file on the FTP server reveals the SSH credentials for user `jnelson`. For privilege escalation, the `passpie` utility on the remote host can be exploited to obtain the password for the `root` user."
date:   2025-10-23 10:10:37 +0200
---

![MetaTwo pwned](/assets/images/htb/machines/metatwo_pwned.png)

# Description
MetaTwo is an easy Linux machine that features a website running Wordpress, which is using a plugin vulnerable to unauthenticated SQL injection ([CVE-2022-0739](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2022-0739)). It can be exploited to reveal the password hash of the Wordpress users which can be cracked to obtain the password for the Wordpress user `manager`. The Wordpress version in use is vulnerable to an XXE Vulnerability in the Media Library ([CVE-2021-29447](https://blog.wpsec.com/wordpress-xxe-in-media-library-cve-2021-29447/)), which can be exploited to obtain credentials for the FTP server. A file on the FTP server reveals the SSH credentials for user `jnelson`. For privilege escalation, the `passpie` utility on the remote host can be exploited to obtain the password for the `root` user.
