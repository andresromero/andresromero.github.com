---
layout: post
title: Clearing chache memory in Linux
---

1. Login as root
2. Run `sync; echo 3 > /proc/sys/vm/drop_caches`

Note: sudo doesn't work it is obligatory to log as root
