---
layout: htb_item
title: "Alert"
os: "Linux"
difficulty: "Easy"
type: "machines"
image: "/assets/images/htb/machines/alert.png"
description: "Alert is an easy-difficulty Linux machine with a website to upload, view, and share markdown files. The site is vulnerable to cross-site scripting (XSS), which is exploited to access an internal page vulnerable to Arbitrary File Read and leveraged to gain access to a password hash. The hash is then cracked to reveal the credentials leveraged to gain `SSH` access to the target. Enumeration of processes running on the system shows a `PHP` file that is being executed regularly, which has excessive privileges for the management group our user is a member of and allows us to overwrite the file for code execution as root."
date:   2025-10-23 10:10:37 +0200
---

![Alert pwned](/assets/images/htb/machines/alert_pwned.png)

# Description
Alert is an easy-difficulty Linux machine with a website to upload, view, and share markdown files. The site is vulnerable to cross-site scripting (XSS), which is exploited to access an internal page vulnerable to Arbitrary File Read and leveraged to gain access to a password hash. The hash is then cracked to reveal the credentials leveraged to gain `SSH` access to the target. Enumeration of processes running on the system shows a `PHP` file that is being executed regularly, which has excessive privileges for the management group our user is a member of and allows us to overwrite the file for code execution as root. 
