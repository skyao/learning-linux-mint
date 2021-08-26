---
title: "酷我音乐"
linkTitle: "酷我音乐"
weight: 473
date: 2021-08-26
description: >
  酷我音乐的 linux 客户端，linux下难得一见的好东西，非常优秀的在线音乐播放器。
---


酷我音乐的 linux 客户端，linux下难得一见的好东西，非常优秀的在线音乐播放器。

## 下载

网站介绍：

https://github.com/LiuLang/kwplayer

酷我音乐的 linux 客户端的介绍: kwplayer是一款运行在linux桌面的网络音乐播放器, 它使用 酷我音乐盒 的音乐资源.

下载地址在这里：

~~https://github.com/LiuLang/kwplayer-packages~~

这个地址已经无效，作者不再维护这个项目并删除了 kwplayer-packages 及其原有的安装包。

在 csdn 找到一个可以下载的地址，可以下载到 kwplayer_3.5.2-1_all.deb：

http://download.csdn.net/download/qq_25897059/9280077

## 安装

解压缩下载的 kwplayer-packages-master.zip 文件，进入解压缩后的目录。

然后按照要求的顺序，先后安装下面三个 deb 文件:

- python3-xlib_0.15-1_all.deb: 这个版本没有下载到，直接在软件管理器中可以找到 python3-xlib 的 0.14版本，实测可用
- ~~python3-keybinder_1.1.2-1_all.deb~~: 找不到下载，发现不安装也可以用，无非就是少一点功能
- kwplayer_3.5.2-1_all.deb