---
title: "[归档]软件安装工具snap"
linkTitle: "[归档]snap"
weight: 99
date: 2021-08-26
description: >
  snap可以方便的安装各种软件
---

备注： snap 感觉很烂，还是不安装了，linux mint 将它刻意隐藏果然是有道理的。

参考：

https://snapcraft.io/docs/installing-snap-on-linux-mint

```bash
sudo mv /etc/apt/preferences.d/nosnap.pref /etc/apt/nosnap.pref.backup

sudo apt update

sudo apt install snapd
```