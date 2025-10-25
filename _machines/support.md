---
layout: htb_item
title: "Support"
os: "Windows"
difficulty: "Easy"
type: "machines"
image: "/assets/images/htb/machines/support.png"
description: "Support is an Easy difficulty Windows machine that features an SMB share that allows anonymous authentication. After connecting to the share, an executable file is discovered that is used to query the machine&amp;amp;amp;amp;#039;s LDAP server for available users. Through reverse engineering, network analysis or emulation, the password that the binary uses to bind the LDAP server is identified and can be used to make further LDAP queries. A user called `support` is identified in the users list, and the `info` field is found to contain his password, thus allowing for a WinRM connection to the machine. Once on the machine, domain information can be gathered through `SharpHound`, and `BloodHound` reveals that the `Shared Support Accounts` group that the `support` user is a member of, has `GenericAll` privileges on the Domain Controller. A Resource Based Constrained Delegation attack is performed, and a shell as `NT Authority\ System` is received."
date:   2025-10-23 10:10:37 +0200
---

![Support pwned](/assets/images/htb/machines/support_pwned.png)

# Description
Support is an Easy difficulty Windows machine that features an SMB share that allows anonymous authentication. After connecting to the share, an executable file is discovered that is used to query the machine&amp;amp;amp;amp;#039;s LDAP server for available users. Through reverse engineering, network analysis or emulation, the password that the binary uses to bind the LDAP server is identified and can be used to make further LDAP queries. A user called `support` is identified in the users list, and the `info` field is found to contain his password, thus allowing for a WinRM connection to the machine. Once on the machine, domain information can be gathered through `SharpHound`, and `BloodHound` reveals that the `Shared Support Accounts` group that the `support` user is a member of, has `GenericAll` privileges on the Domain Controller. A Resource Based Constrained Delegation attack is performed, and a shell as `NT Authority\ System` is received.