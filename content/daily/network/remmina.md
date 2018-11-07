---
date: 2018-11-07T13:05:00+08:00
title: Remmina
menu:
  main:
    parent: "daily-network"
weight: 341
description : "Remmina"
---

Remmina 是一个远程桌面软件。

## 安装

可以通过软件管理器直接安装，"开始菜单" -> "系统管理" -> "软件管理器"，搜索 `remmina`：

![](images/remmina_search.jpg)

需要使用软件管理器安装 remmina 和 插件:

- remmina
- remmina-plugin-rdp: 这个一定要安装,连接windows桌面就是走 RDP 协议
- remmina-plugin-vnc

## 使用

### 连接 windows

安装完成之后, 打开 remmina, "connection" -> "new", Protocol 选 "RDP - Remote Desktop Protocol", 设置链接参数和账号, 就可以连接到 windows 桌面.

ubuntu18.04

https://www.techrepublic.com/article/how-to-enable-remote-desktop-connections-in-ubuntu-18-04/