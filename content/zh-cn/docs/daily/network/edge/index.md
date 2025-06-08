---
title: "安装微软Edge浏览器"
linkTitle: "Edge浏览器"
weight: 60
date: 2021-08-26
description: >
  微软Edge浏览器是目前最好用的浏览器了，我用它替换了google的chrome
---

## 安装

### 直接下载安装

https://www.microsoft.com/zh-tw/edge/download

选择 deb 格式下载安装即可。

### apt安装

参考：

https://linuxhint.com/install-microsoft-edge-browser-ubuntu/

安装方式：

```bash
sudo apt install software-properties-common apt-transport-https wget
wget -q https://packages.microsoft.com/keys/microsoft.asc -O- | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://packages.microsoft.com/repos/edge stable main"
sudo apt update
sudo apt install microsoft-edge-stable

```

