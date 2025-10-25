---
layout: htb_item
title: "Blurry"
os: "Linux"
difficulty: "Medium"
type: "machines"
image: "/assets/images/htb/machines/blurry.png"
description: "Blurry is a medium-difficulty Linux machine that features DevOps-related vectors surrounding machine learning. The foothold is comprised of a series of CVEs recently disclosed about the ClearML suite. The service provides a web platform, a fileserver, and an API; all of which contain vulnerabilities (`[CVE-2024-24590](https://nvd.nist.gov/vuln/detail/CVE-2024-24590)` - `[CVE-2024-24595](https://nvd.nist.gov/vuln/detail/CVE-2024-24595)`) that can be chained together for remote code execution. Once a shell on the target is obtained, a program that can be run with `sudo` is discovered. The program loads arbitrary `PyTorch` models to evaluate them against a protected dataset. While it is known that such models are susceptible to insecure deserialisation, `fickling` is used to scan the dataset for insecure `pickle` files , prior to loading the model. Malicious code can be injected into a model, using `runpy` to bypass the `fickling` checks."
date:   2025-10-23 10:10:37 +0200
---

![Blurry pwned](/assets/images/htb/machines/blurry_pwned.png)

# Description
Blurry is a medium-difficulty Linux machine that features DevOps-related vectors surrounding machine learning. The foothold is comprised of a series of CVEs recently disclosed about the ClearML suite. The service provides a web platform, a fileserver, and an API; all of which contain vulnerabilities (`[CVE-2024-24590](https://nvd.nist.gov/vuln/detail/CVE-2024-24590)` - `[CVE-2024-24595](https://nvd.nist.gov/vuln/detail/CVE-2024-24595)`) that can be chained together for remote code execution. Once a shell on the target is obtained, a program that can be run with `sudo` is discovered. The program loads arbitrary `PyTorch` models to evaluate them against a protected dataset. While it is known that such models are susceptible to insecure deserialisation, `fickling` is used to scan the dataset for insecure `pickle` files , prior to loading the model. Malicious code can be injected into a model, using `runpy` to bypass the `fickling` checks.
