---
layout: htb_item
title: "Runner"
os: "Linux"
difficulty: "Medium"
type: "machines"
image: "/assets/images/htb/machines/runner.png"
description: "Runner is a medium difficulty Linux box that contains a vulnerability ([CVE-2023-42793](https://nvd.nist.gov/vuln/detail/CVE-2023-42793)) in `TeamCity`. This vulnerability allows users to bypass authentication and extract an API token, which can be used to enable debug features for executing system commands. By gaining access to a `TeamCity` docker container and compressing the `HSQLDB` database files, we can extract credentials for the user `matthew` and find an `SSH` key for `john`. After cracking the password, we can authenticate on the host filesystem. Upon inspecting the `/etc/hosts` file, we discover a running `Portainer` instance. Using `matthew&amp;#039;s` credentials, we access the subdomain externally. While authenticated, we find that we can create images, but our privileges are limited. After checking the version of `runc` on the host, we exploit a vulnerability ([CVE-2024-21626](https://nvd.nist.gov/vuln/detail/CVE-2024-21626)) through the image build function of `Portainer`, which allows us to create a SUID bash file on the host."
date:   2025-10-23 10:10:37 +0200
---

![Runner pwned](/assets/images/htb/machines/runner_pwned.png)

# Description
Runner is a medium difficulty Linux box that contains a vulnerability ([CVE-2023-42793](https://nvd.nist.gov/vuln/detail/CVE-2023-42793)) in `TeamCity`. This vulnerability allows users to bypass authentication and extract an API token, which can be used to enable debug features for executing system commands. By gaining access to a `TeamCity` docker container and compressing the `HSQLDB` database files, we can extract credentials for the user `matthew` and find an `SSH` key for `john`. After cracking the password, we can authenticate on the host filesystem. Upon inspecting the `/etc/hosts` file, we discover a running `Portainer` instance. Using `matthew&amp;#039;s` credentials, we access the subdomain externally. While authenticated, we find that we can create images, but our privileges are limited. After checking the version of `runc` on the host, we exploit a vulnerability ([CVE-2024-21626](https://nvd.nist.gov/vuln/detail/CVE-2024-21626)) through the image build function of `Portainer`, which allows us to create a SUID bash file on the host.
