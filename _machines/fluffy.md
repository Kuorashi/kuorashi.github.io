---
layout: htb_item
title: "Fluffy"
os: "Windows"
difficulty: "Easy"
type: "machines"
image: "/assets/images/htb/machines/fluffy.png"
description: "`Fluffy` is an easy-difficulty Windows machine designed around an assumed breach scenario, where credentials for a low-privileged user are provided. By exploiting [CVE-2025-24071](https://nvd.nist.gov/vuln/detail/CVE-2025-24071), the credentials of another low-privileged user can be obtained. Further enumeration reveals the existence of ACLs over the `winrm_svc` and `ca_svc` accounts. `WinRM` can then be used to log in to the target using the `winrc_svc` account. Exploitation of an Active Directory Certificate service (`ESC16`) using the `ca_svc` account is required to obtain access to the `Administrator` account."
date:   2025-10-23 10:10:37 +0200
---

![Fluffy pwned](/assets/images/htb/machines/fluffy_pwned.png)

# Description
`Fluffy` is an easy-difficulty Windows machine designed around an assumed breach scenario, where credentials for a low-privileged user are provided. By exploiting [CVE-2025-24071](https://nvd.nist.gov/vuln/detail/CVE-2025-24071), the credentials of another low-privileged user can be obtained. Further enumeration reveals the existence of ACLs over the `winrm_svc` and `ca_svc` accounts. `WinRM` can then be used to log in to the target using the `winrc_svc` account. Exploitation of an Active Directory Certificate service (`ESC16`) using the `ca_svc` account is required to obtain access to the `Administrator` account.
