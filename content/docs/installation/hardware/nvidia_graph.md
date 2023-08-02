---
title: "Nvidia显卡驱动安装"
linkTitle: "Nvidia显卡"
weight: 20
date: 2022-03-30
description: >
  介绍Linux Mint下Nvidia显卡的驱动安装
---



## 正常安装

"开始菜单" -> "系统管理" -> "驱动管理器"，

Linux Mint 会先做一次系统更新检查，然后给出可以安装的驱动列表。

只要简单选择需要的驱动版本，然后安装即可，如下图：

![](images/nvidia-graph.png)



## 特殊情况

### 无法打开系统设置界面

有时会遇到无法打开系统设置界面的情况，导致无法进入设备管理器。

此时，可以在桌面右键，打开终端，然后执行 `/usr/bin/cinnamon-settings` 命令，即可打开设置界面。

### 无法进入图形界面

某一次更换显卡时，从adm rx580显卡换到nvidia 3070显卡，遇到无法显示图形界面的情况，黑色屏幕上只有左上角有一个光标一闪一闪。而且网络也莫名其妙的不通，无法ssh。

解决方法：

1. 解决无法ssh的问题：按 `ctr+alt+F` 可以显示出 terminal 界面，输入用户名/密码就可以登录。期间如果再次黑屏，可以继续 按 `ctr+alt+F` 。登录之后，网络也就通了。

2. 安装 nvidia 显卡驱动

   ```bash
   sudo apt update
   sudo apt-cache search nvidia-driver
   sudo apt install nvidia-driver-525
   ```

   安装完成之后重启即可，正常显示图形界面。

参考资料：

- [ubuntu20.04 安装nvidia显卡驱动后无法启动系统的解决办法](https://blog.csdn.net/csdnlg112/article/details/124718836)

  
