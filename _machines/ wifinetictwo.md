---
layout: htb_item
title: "Wifinetictwo"
os: "Linux"
difficulty: "Medium"
type: "machines"
image: "/assets/images/htb/machines/wifinetictwo.png"
description: "WifineticTwo is a medium-difficulty Linux machine that features OpenPLC running on port 8080, vulnerable to Remote Code Execution through the manual exploitation of `[CVE-2021-31630](https://nvd.nist.gov/vuln/detail/CVE-2021-31630)`. After obtaining an initial foothold on the machine, a WPS attack is performed to acquire the Wi-Fi password for an Access Point (AP). This access allows the attacker to target the router running `OpenWRT` and gain a root shell via its web interface."
date:   2025-10-23 10:10:37 +0200
---

![Wifinetictwo pwned](/assets/images/htb/machines/wifinetictwo_pwned.png)

# Description
WifineticTwo is a medium-difficulty Linux machine that features OpenPLC running on port 8080, vulnerable to Remote Code Execution through the manual exploitation of `[CVE-2021-31630](https://nvd.nist.gov/vuln/detail/CVE-2021-31630)`. After obtaining an initial foothold on the machine, a WPS attack is performed to acquire the Wi-Fi password for an Access Point (AP). This access allows the attacker to target the router running `OpenWRT` and gain a root shell via its web interface.
