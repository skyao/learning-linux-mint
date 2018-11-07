---
date: 2018-11-07T13:05:00+08:00
title: Shutter
menu:
  main:
    parent: "daily-tool"
weight: 324
description : "Shutter"
---

shutter 是 linux 下非常好用的一款截图软件，功能强大。

## 安装

可以通过软件管理器直接安装，"开始菜单" -> "系统管理" -> "软件管理器"，搜索 `shutter`：

![](images/shutter_search.jpg)

点击安装即可。

## 配套软件

需要安装几个配套的软件，才能使用 shutter 全面的功能:

- gnome-web-photo: a tool to generate full-size image files and thumbnails from HTML files and web pages 用于抓取整个网页
- libgoo-canvas-perl: canvas widget 用于编辑抓图文件,增加标注等，这个必须安装，不然非常的不方便，截图之后加个箭头写个标注是常见的事。

在ubuntu16.04、linux mint18下可以直接通过apt-get或者软件管理器安装。

在ubuntu18.04、linux mint19下，libgoo-canvas-perl 类库不能直接安装，需要自行下载手工安装。

libgoo-canvas-perl：

- [libgoocanvas-common](https://launchpad.net/ubuntu/+archive/primary/+files/libgoocanvas-common_1.0.0-1_all.deb)
- [libgoocanvas3](https://launchpad.net/ubuntu/+archive/primary/+files/libgoocanvas3_1.0.0-1_amd64.deb)
- [libgoo-canvas-perl](https://launchpad.net/ubuntu/+archive/primary/+files/libgoo-canvas-perl_0.06-2ubuntu3_amd64.deb)

gnome-web-photo：

- 下载地址： [official download webpage for gnome-web-photo for Ubuntu 16.04](https://packages.ubuntu.com/xenial/amd64/gnome-web-photo/download).

关闭正在运行的Shutter窗口，重新启动Shutter。

参考资料：

- [Ubuntu 18.04中截图工具Shutter的编辑按钮不可用的解决办法](https://www.cnblogs.com/jaxu/p/9561992.html)

- [How to enable globe in Shutter in Ubuntu 18.04?](https://askubuntu.com/questions/1082309/how-to-enable-globe-in-shutter-in-ubuntu-18-04)

## 设置

### 图片导出格式

打开 shutter，菜单中点 "编辑" -> "Preference" 打开 首选项，点"主要"。

图片格式中，默认时png格式，文件大小会稍微嫌大，可以设置为 jpg 格式，然后图片质量设置为 80%.

