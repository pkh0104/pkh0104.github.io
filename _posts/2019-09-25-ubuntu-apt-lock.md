---
title: "Could not get lock /var/lib/apt/lists/lock when apt-get update"
data: 2019-09-25 00:41:00 -0400
categories: ubuntu desktop error
---

Lists of packages downloaded from the Ubuntu servers are  in the /var/lib/apt/lists.  
There is no harm with revmoving all contents in this directory.

```bash
$ sudo rm -rf /var/lib/apt/lists/*
$ sudo apt-get update
```
