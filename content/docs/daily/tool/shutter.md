---
title: "截图软件Shutter"
linkTitle: "Shutter"
weight: 424
date: 2021-08-26
description: >
  shutter是linux下非常好用的一款截图软件，功能强大。
---

## 安装

最新的版本需要通过 PPA 方式来安装：

```bash
sudo add-apt-repository ppa:linuxuprising/shutter
sudo apt-get update
sudo apt install shutter
```

参考：

- [New Shutter PPA For Ubuntu 21.04, 20.10, 20.04 And 18.04 | Linux Mint 20.x And 19.x](https://www.linuxuprising.com/2018/10/shutter-removed-from-ubuntu-1810-and.html)

### 配套软件包

gnome-web-photo 包让shutter能够抓取完整的网站页面：

```bash
sudo apt install gnome-web-photo
```

使用时点击shutter界面上的 "网页" ，然后输入 URL 就可以截图。

## 设置

### 图片导出格式

打开 shutter，菜单中点 "首选项" --> "主要"。

图片格式中，默认时png格式，文件大小会稍微嫌大，可以设置为 jpg 格式，然后图片质量设置为 80%.

