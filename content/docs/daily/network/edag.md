---
title: "微软Edge浏览器"
linkTitle: "Edge浏览器"
weight: 447
date: 2021-08-26
description: >
  微软Edge浏览器
---


微软Edge浏览器

## 安装

https://www.microsoftedgeinsider.com/zh-cn/download/

PPA安装：

```bash
## Setup
curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
sudo install -o root -g root -m 644 microsoft.gpg /etc/apt/trusted.gpg.d/
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/edge stable main" > /etc/apt/sources.list.d/microsoft-edge-dev.list'
sudo rm microsoft.gpg
## Install
sudo apt update
sudo apt install microsoft-edge-dev
```