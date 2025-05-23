---
title: "Linux Mint的安装过程"
linkTitle: "安装过程"
weight: 201
date: 2021-08-26
description: >
  Linux Mint 的安装过程
---


Linux Mint 的安装比较简单，安装速度也非常快。

但是期间还是有一些事情要小心。

## 安装前准备

从 Linux Mint 的下载页面下载 Linux Mint 22 的 Cinnamon 的64位版本。

https://linuxmint.com/download.php

https://www.linuxmint.com/download_all.php

之后使用各种工具将下载下来的 ISO 文件制作成启动 U 盘进行安装，推荐 rufus。

## 安装

安装时，在选择安装盘符时需要注意：

1. 最好单独再建立一个 EFI 分区，不要使用原有 windows 的EFI分区，大小一般128M足以
2. 由于docker的原因，建议不建立交换分区
3. 特别注意：启动信息那里一定要选择我们为linux新建的 EFI 分区

安装过程中，如果提醒是否要下载更新，选择 no。原因是安装时使用的源是 Linux Mint 默认的源，对于国内用户速度很慢。建议选择在安装完成之后，再设置好国内速度快的源，然后再更新，速度就非常好。

### 语言选择

推荐安装时选择 english，安装完成后单独安装中文输入法可以输入中文就好，界面还是保持英文会更方便一些。

### 自动登录

安装过程在设置用户名密码时，有个是否自动登录的选项，如果是自己机器平时也不需要考虑安全性，选上，可以省事加开机更快。

## 安装完操作

### 设置软件源

安装完成，进入桌面之后的第一件事情，就是设置软件源。

"开始菜单" -> "系统管理" -> "软件源"，然后就可以设置镜像，包括主要和基础两个：

![](images/software_sources.jpg)

选择时会自动提供速度测试，可以根据测试出来的速度情况选择一个速度比较好的源，我这边选择的是 ustc 和 dgut 。

{{% alert title="Warning" color="warning" %}}
注意一定要先更新软件源之后，再开始各种配置和安装，否则国外源时速度不好时非常浪费时间。
{{% /alert %}}

### 更新系统和内核

在设置好软件源之后，再使用操作系统自带的 "更新管理器" 进行系统更新，包括内核更新。

{{% pageinfo color="primary" %}}
我个人习惯是直接更新到最新版本的内核。
{{% /pageinfo %}}

### 额外提示

`Alt+F7` 是移动窗口的快捷键，在某些特殊情况下，如果屏幕分辨率因故被设置的太低，会出现窗口太长而无法在屏幕上显示完整，导致某些关键的输入和按钮在屏幕外点不到。

此时就需要使用 `Alt+F7` 快捷键来移动窗口，不然被卡死会非常憋屈。
