---
layout: htb_item
title: "Administrator"
os: "Windows"
difficulty: "Medium"
type: "machines"
image: "/assets/images/htb/machines/administrator.png"
description: "`Administrator` is a medium-difficulty Windows machine designed around a complete domain compromise scenario, where credentials for a low-privileged user are provided. To gain access to the `michael` account, ACLs (Access Control Lists) over privileged objects are enumerated, leading us to discover that the user `olivia` has `GenericAll` permissions over `michael`, allowing us to reset his password. With access as `michael`, it is revealed that he can force a password change on the user `benjamin`, whose password is reset. This grants access to `FTP` where a `backup.psafe3` file is discovered, cracked, and reveals credentials for several users. These credentials are sprayed across the domain, revealing valid credentials for the user `emily`. Further enumeration shows that `emily` has `GenericWrite` permissions over the user `ethan`, allowing us to perform a targeted Kerberoasting attack. The recovered hash is cracked and reveals valid credentials for `ethan`, who is found to have `DCSync` rights ultimately allowing retrieval of the `Administrator` account hash and full domain compromise."
date:   2025-10-23 10:10:37 +0200
---

![Administrator pwned](/assets/images/htb/machines/administrator_pwned.png)

# Description
`Administrator` is a medium-difficulty Windows machine designed around a complete domain compromise scenario, where credentials for a low-privileged user are provided. To gain access to the `michael` account, ACLs (Access Control Lists) over privileged objects are enumerated, leading us to discover that the user `olivia` has `GenericAll` permissions over `michael`, allowing us to reset his password. With access as `michael`, it is revealed that he can force a password change on the user `benjamin`, whose password is reset. This grants access to `FTP` where a `backup.psafe3` file is discovered, cracked, and reveals credentials for several users. These credentials are sprayed across the domain, revealing valid credentials for the user `emily`. Further enumeration shows that `emily` has `GenericWrite` permissions over the user `ethan`, allowing us to perform a targeted Kerberoasting attack. The recovered hash is cracked and reveals valid credentials for `ethan`, who is found to have `DCSync` rights ultimately allowing retrieval of the `Administrator` account hash and full domain compromise.
