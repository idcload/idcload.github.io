---
layout: post
title: Debian automatic upgrades
category: posts
---

Make sure that unattended-upgrades is installed and then enable the installation of updates (as root):

```bash
apt install unattended-upgrades
dpkg-reconfigure -plow unattended-upgrades
```
