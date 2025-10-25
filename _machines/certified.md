---
layout: htb_item
title: "Certified"
os: "Windows"
difficulty: "Medium"
type: "machines"
image: "/assets/images/htb/machines/certified.png"
description: "`Certified` is a medium-difficulty Windows machine designed around an assumed breach scenario, where credentials for a low-privileged user are provided. To gain access to the `management_svc` account, ACLs (Access Control Lists) over privileged objects are enumerated leading us to discover that `judith.mader` which has the `write owner` ACL over `management` group, management group has `GenericWrite` over the `management_svc` account where we can finally authenticate to the target using `WinRM` obtaining the user flag. Exploitation of the Active Directory Certificate Service (ADCS) is required to get access to the `Administrator` account by abusing shadow credentials and `ESC9`."
date:   2025-10-23 10:10:37 +0200
---

![Certified pwned](/assets/images/htb/machines/certified_pwned.png)

# Description
`Certified` is a medium-difficulty Windows machine designed around an assumed breach scenario, where credentials for a low-privileged user are provided. To gain access to the `management_svc` account, ACLs (Access Control Lists) over privileged objects are enumerated leading us to discover that `judith.mader` which has the `write owner` ACL over `management` group, management group has `GenericWrite` over the `management_svc` account where we can finally authenticate to the target using `WinRM` obtaining the user flag. Exploitation of the Active Directory Certificate Service (ADCS) is required to get access to the `Administrator` account by abusing shadow credentials and `ESC9`.
