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

## 版本选择

我习惯使用 Cinnamon 版本。

关于 LMDE 的额外说明：

我尝试过使用 LMDE7, 先后在两台主力开发机器上使用，整体挺好用的。但后来陆陆续续发现各种小地方不舒服，又耗费非常大的力气重新安装会普通版本。个人建议不要折腾 LMDE 版本。我以后应该也不会再用 LMDE。

## 安装前准备

从 Linux Mint 的下载页面下载 Linux Mint 22 的 Cinnamon 的64位版本。

https://linuxmint.com/download.php

https://www.linuxmint.com/download_all.php

之后使用各种工具将下载下来的 ISO 文件制作成启动 U 盘进行安装，推荐 rufus。Linux mint 下直接用系统自带的 iso 刻盘工具写入 u 盘即可。

## 安装

安全起见，我一般都是全新安装，不做升级安装，尤其是跨大版本的升级安装。

安装时，在选择安装盘符时需要注意：

1. 最好单独再建立一个 EFI 分区，不要使用原有 windows 的EFI分区，大小一般128M足以
2. 交换分区不用太大，16GB足以。
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

选择时会自动提供速度测试，可以根据测试出来的速度情况选择一个速度比较好的源，我这边选择的是 aliyun 和 huaweicloud 。

{{% alert title="Warning" color="warning" %}}
注意一定要先更新软件源之后，再开始各种配置和安装，否则国外源时速度不好时非常浪费时间。
{{% /alert %}}

### 更新系统和内核

在设置好软件源之后，再使用操作系统自带的 "更新管理器" 进行系统更新，包括内核更新。

{{% pageinfo color="primary" %}}
我个人习惯是直接更新到最新版本的内核。
{{% /pageinfo %}}

重启之后，再次进入 更新管理器，删除旧的内核。

### 软件管理器

最新版本的 linux mint（如 22.3）在安装后第一次打开 软件管理器 时会卡住。表现为：打开 software manager，一直转圈圈，提示 generating cache, one moment，但等了很久也没有完成。

问题所在： 新版软件管理器在生成缓存阶段会顺带扫描 Flatpak 源，而默认 Flathub（dl.flathub.org）在国内基本连不上，会让它挂着等网络超时。

```bash
ss -tpn | grep -E "mintinstall|python3" # 看它有没有挂着对外 TCP 连接
4116
4119
ESTAB 0 0 [240e:46d:ac00:2a84:d082:c090:d662:e259]:47552 [2a04:4e42:68::347]:443 users:(("mintinstall",pid=4119,fd=30))
ESTAB 0 0 [240e:46d:ac00:2a84:d082:c090:d662:e259]:47564 [2a04:4e42:68::347]:443 users:(("mintinstall",pid=4119,fd=37))
```

2a04:4e42::/32 是 Fastly 的 CDN 段，也就是 dl.flathub.org（Flathub 的下载服务器）。mintinstall 生成缓存时，除了 apt，还会刷新 Flathub 的 appstream 元数据——它在后台通过 Flatpak 去拉 Flathub，而 Flathub 的国际线路（尤其你这边还走 IPv6）在国内基本是"TCP 能连上、但 HTTP 数据半天流不动"，于是 mintinstall 就永远挂在那句 "Generating cache" 上。

最简单的办法是先直接把 flathub 源摘掉就行（注意：只删 remote，不是卸载 flatpak 本体）：

```bash
sudo flatpak remote-delete --system flathub
```

然后重启软件管理器：

```bash
pkill -f mintinstall
rm -rf ~/.cache/mintinstall
mintinstall
```

### 额外提示

`Alt+F7` 是移动窗口的快捷键，在某些特殊情况下，如果屏幕分辨率因故被设置的太低，会出现窗口太长而无法在屏幕上显示完整，导致某些关键的输入和按钮在屏幕外点不到。

此时就需要使用 `Alt+F7` 快捷键来移动窗口，不然被卡死会非常憋屈。
