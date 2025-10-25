---
layout: htb_item
title: "Cap"
os: "Linux"
difficulty: "Easy"
type: "machines"
image: "/assets/images/htb/machines/cap.png"
description: "Cap is an easy difficulty Linux machine running an HTTP server that performs administrative functions including performing network captures. Improper controls result in Insecure Direct Object Reference (IDOR) giving access to another user's capture. The capture contains plaintext credentials and can be used to gain foothold. A Linux capability is then leveraged to escalate to root."
date:   2025-10-23 10:10:37 +0200
---

![Cap pwned](/assets/images/htb/machines/cap_pwned.png)

# Description
Cap is an easy difficulty Linux machine running an HTTP server that performs administrative functions including performing network captures. Improper controls result in Insecure Direct Object Reference (IDOR) giving access to another user's capture. The capture contains plaintext credentials and can be used to gain foothold. A Linux capability is then leveraged to escalate to root.