---
title: "WhiteSur主题"
linkTitle: "WhiteSur"
weight: 222
date: 2021-08-27
description: >
  模仿Macos 11 Big Sur的WhiteSur主题
---

## 介绍

- https://github.com/vinceliuice/WhiteSur-gtk-theme：主题作者的github

![](https://github.com/vinceliuice/WhiteSur-gtk-theme/raw/pictures/pictures/macbook.png)

## 安装WhiteSur主题

### 手工下载安装主题

WhiteSur主题相关的文件可以从下面地址下载：

#### WhiteSur Gtk Theme

这是 WhiteSur Gtk 主题。

地址：https://www.gnome-look.org/p/1403328/

下载文件:

- WhiteSur-dark.tar.xz
- WhiteSur-light.tar.xz
- WhiteSur-light-solid.tar.xz
- WhiteSur-dark-solid.tar.xz

> 备注：看介绍说NVIDIA的显卡适合用 solid 的主题，不了解为什么，都下载下来

#### WhiteSur-icon-theme

这是仿big sur的图标。

地址：https://www.gnome-look.org/p/1405756/

下载文件：

- 01-WhiteSur.tar.xz

#### macOS Big Sur  cursors

这是仿big sur的鼠标指针。

地址：https://www.gnome-look.org/p/1408466/

下载文件：

- macOSBigSur.tar.gz

#### 主题文件部署

进入当前用户的 home 目录，建立以下文件夹：

```bash
cd
mkdir .themes
mkdir .icons
```

将前面下载的主题文件和icon文件（包括cursors的图标）都解压后复制到上面两个目录中。

#### 设置主题为WhiteSur

打开系统的 "主题" 设置，将 窗口边框 / 图标  / 控件 / 鼠标指针 / 桌面 都修改为 `WhiteSur`。

>  备注：light和dark看喜欢，我一般喜欢设置 dark，长时间用不累眼。

## 调整Linux Mint的面板

在安装dock效仿macos之前，先要将Linux Mint的面板从默认的底部移动到顶部，将底部的空间让出来给 dock。

然后继续对linux mint的面板进行设置：

- 修改面板图标

    左上角的LM图标，可以修改为mac的图标。在LM图标上右键点配置，就可以修改图标，而且linux mint目录下的图标中就有一个现成的 mac 的图标，直接可以使用

- 修改面板高度

    在面板上右键，点 面板配置，将面板高度从默认的40修改为最小的20。

- 将自动隐藏面板设置为智能隐藏。

## 设置Mac壁纸

为了和macos的界面尽量一致，同时也营造macos的感觉，壁纸是必不可少的。

https://512pixels.net/projects/default-mac-wallpapers-in-5k/#jp-carousel-19693

这个地址里面有mac各个版本的壁纸可供下载，5k/6k的分辨率足够清晰，下载 big sur 和 Monterey 经典的彩色壁纸。

主题搞定！此时界面已经美化了很多。

## 其他补充

### desktop cube

打开 extension（扩展），在下载中找到 desktop cube，双击安装，然后点 + 启用。

> 备注：如果安装是报错说连接被重置，请开启科学上网。

这是是用于workspace切换时的转场动画，挺酷炫的。

### 减少桌面图标

{{% pageinfo color="primary" %}}
桌面上东西太多会影响观感。
{{% /pageinfo %}}

在桌面上右键，点"自定义" -> "桌面设置"，取消以下内容的勾选：

- 计算机
- 主目录
- 已挂载的驱动器
- 网络：默认就是不勾选的
- 显示缺少的显示器的图标

