---
layout: htb_item
title: "UnderPass"
os: "Linux"
difficulty: "Easy"
type: "machines"
image: "/assets/images/htb/machines/underpass.png"
description: "Underpass is an Easy Linux machine starting with a default Apache Ubuntu page. This leads the attacker to enumerate the machine&#039;s UDP ports for alternative attack vectors. The attacker can enumerate SNMP and discover that `Daloradius` is running on the remote machine, and the operators panel can be accessed using the default credentials. Inside the panel, the password hash for the user `svcMosh` is stored, and it&#039;s crackable. Then, the attacker can log in to the remote machine using SSH with the credentials they have obtained. The user `svcMosh` is configured to run `mosdh-server` as `root`, which allows the attacker to connect to the server from their local machine and interact with the remote machine as the `root` user."
date:   2025-10-23 10:10:37 +0200
---

![UnderPass pwned](/assets/images/htb/machines/underpass_pwned.png)

# Description
Underpass is an Easy Linux machine starting with a default Apache Ubuntu page. This leads the attacker to enumerate the machine&amp;amp;amp;amp;#039;s UDP ports for alternative attack vectors. The attacker can enumerate SNMP and discover that `Daloradius` is running on the remote machine, and the operators panel can be accessed using the default credentials. Inside the panel, the password hash for the user `svcMosh` is stored, and it&amp;amp;amp;amp;#039;s crackable. Then, the attacker can log in to the remote machine using SSH with the credentials they have obtained. The user `svcMosh` is configured to run `mosdh-server` as `root`, which allows the attacker to connect to the server from their local machine and interact with the remote machine as the `root` user.
