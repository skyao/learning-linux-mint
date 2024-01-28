---
title: "安装配置VMWare Player"
linkTitle: "VMWare Player"
weight: 470
date: 2021-09-10
description: >
  安装配置VMWare Player
---



## 准备工作

参考：

https://linuxize.com/post/how-to-install-vmware-workstation-player-on-ubuntu-20-04/

先安装：

```bash
sudo apt install build-essential linux-headers-generic
```

## 下载安装

### 下载

vmware player官方页面：

https://www.vmware.com/products/workstation-player.html

下载地址：https://customerconnect.vmware.com/en/downloads/info/slug/desktop_end_user_computing/vmware_workstation_player/16_0

目前最新版本是 16.1.2. 下载 "VMware Workstation 16.1.2 Player for Linux 64-bit".

### 安装

```bash
chmod +x VMware-Player-16.1.2-17966106.x86_64.bundle 
sudo ./VMware-Player-16.1.2-17966106.x86_64.bundle
```

然后启动vmware player，同意协议，选择非商业用户。



