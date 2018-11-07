---
date: 2018-11-07T13:05:00+08:00
title: Pidgin
menu:
  main:
    parent: "daily-im"
weight: 362
description : "Pidgin"
---

Linux Mint 自带 pidgin，版本是 2.10。

## 从源码编译

如果想升级到最新版本，或者，因为某些特殊原因导致内置版本的 pidgin 不可使用，就需要考虑从源码开始编译。

> 特别说明： 手工编译升级 pidgin 和 lync插件 pidpin-sipe 到最新版本之后，开始可以使用，后面不久就莫名其妙的出问题，表现为 pidgin 启动之后无法找到 pidpin-sipe 导致无法支持 office communicator 协议，但是系统又显示 pidpin-sipe 已经安装。因此建议，别折腾了，直接用仓库自带版本的 pidgin 和 pidpin-sipe 就好。

安装前，请使用软件管理器卸载 pidgin，或者直接 `sudo apt-get remove pidgin` 。

### 下载源码

pidgin 源代码下载地址：

https://sourceforge.net/projects/pidgin/

目前下载的最新版本是 2.11.0 （Linux Mint 18 内置的时2.10版本）

### 编译准备

编译前的准备工作，安装编译工具：

```bash
sudo apt-get install build-essential
sudo apt-get install checkinstall
```

### 编译安装

解压缩下载的源代码文件，执行 `./configure` 命令，期间通常会因为找不到header文件而报错，需要逐个排查。

下面是我安装过程中发现需要安装的包：

```bash
sudo apt-get install libgtk2.0-dev libgstreamer1.0-dev libfarstream-0.2-dev libgstreamer-plugins-base1.0-dev libgtkspell-dev libxss-dev libidn11-dev libmeanwhile-dev libavahi-client-dev libavahi-glib-dev network-manager-dev libperl-dev tcl-dev tk-dev
```

备注：因为我是先编译安装 pidgin-spid 插件的，在上面的安装操作之前有做下面的安装，所以有可能下面这些类库也是需要的，建议一起安装。

```bash
sudo apt-get install libpurple-dev libtool intltool pkg-config libglib2.0-dev libxml2-dev libnss3-dev libssl-dev libkrb5-dev libnice-dev libgstreamer0.10-dev
```

准备就绪之后，通过标准命令编译安装：

```bash
./configure
make
sudo make install
```

### 配置启动器

比较奇怪的是，安装完成之后，系统中找不到 pidgin 的启动器，很不方便。

因此需要自己动手新建 pidgin 的启动器，在桌面上右键,"在此创建一个新的启动器"，设置如下：

![](images/pidgin_launcher.jpg)

logo文件是在 bing 搜索找到的，可以自己换成喜欢的，默认logo太丑。

点OK之后，会提示是否加入系统菜单，当然选 yes 了。之后菜单和 gnome do 都可以找到 pidgin 的这个启动器。