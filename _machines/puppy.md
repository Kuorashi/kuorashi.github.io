---
layout: htb_item
title: "Puppy"
os: "Windows"
difficulty: "Medium"
type: "machines"
image: "/assets/images/htb/machines/puppy.png"
description: "Puppy is a Medium Difficulty machine that features a non-default SMB share called `DEV`. With the provided credentials for user `levi.james`, enumeration of the domain is possible. The enumeration reveals that this user has `GenericWrite` privileges over the `Developers` group. After adding Levi to this group, we can access the previously inaccessible `DEV` share. This share contains the backup of a `KeePass` database, which we can download, export the hash of and crack. The database reveals a plethora of username and password combinations. A password spray attack shows that one of the passwords is valid for user `Ant.Edwards`. Furthermore, this new user has `GenericAll` privileges over the user `Adam.Silver`, which allow us to change their password to a password of our choice. After the password is changed, we must re-enable Adam's account, as it has been disabled, which then allows us to connect to the remote system over WinRM. Lateral movement is achieved by finding the backup of a website, which contains credentials for user `Steph.cooper`. Finally, privileges are escalated through `DPAPI` credentials that are decrypted using Steph's password. The credentials revealed belong to `Steph.cooper_adm`, presumably the Administrative account of Steph, and a connection can be made over WinRM."
date:   2025-10-23 10:10:37 +0200
---

![Puppy pwned](/assets/images/htb/machines/puppy_pwned.png)

# Description
Puppy is a Medium Difficulty machine that features a non-default SMB share called `DEV`. With the provided credentials for user `levi.james`, enumeration of the domain is possible. The enumeration reveals that this user has `GenericWrite` privileges over the `Developers` group. After adding Levi to this group, we can access the previously inaccessible `DEV` share. This share contains the backup of a `KeePass` database, which we can download, export the hash of and crack. The database reveals a plethora of username and password combinations. A password spray attack shows that one of the passwords is valid for user `Ant.Edwards`. Furthermore, this new user has `GenericAll` privileges over the user `Adam.Silver`, which allow us to change their password to a password of our choice. After the password is changed, we must re-enable Adam's account, as it has been disabled, which then allows us to connect to the remote system over WinRM. Lateral movement is achieved by finding the backup of a website, which contains credentials for user `Steph.cooper`. Finally, privileges are escalated through `DPAPI` credentials that are decrypted using Steph's password. The credentials revealed belong to `Steph.cooper_adm`, presumably the Administrative account of Steph, and a connection can be made over WinRM.
