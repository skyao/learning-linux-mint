---
title: "截图软件Shutter"
linkTitle: "Shutter"
weight: 30
date: 2021-08-26
description: >
  shutter是linux下非常好用的一款截图软件，功能强大。
---

## 介绍

https://shutter-project.org/

Shutter是一个功能丰富的屏幕截图程序，适用于基于Linux的操作系统，如Ubuntu。你可以对一个特定的区域、窗口、整个屏幕，甚至是一个网站进行截图--对其应用不同的效果，在上面画画以突出重点，然后上传到图片托管网站，所有这些都在一个窗口内完成。Shutter是免费的，开源的，并在GPL v3下许可。

### 截图

Shutter允许你捕捉屏幕上的几乎任何东西，而不会失去对屏幕截图的控制（标签式界面）。下面是你可以用Shutter做的事情的概述。

- 捕捉特定区域

  这允许你在屏幕上选择一个任意的区域，只捕捉那些你真正需要的部分。屏幕可以被放大，所选区域可以被调整大小或移动。

- 捕捉桌面

  Shutter不仅可以捕获你桌面（或工作区）上的所有内容，它还支持多显示器设置，例如，捕获活动显示器。

- 捕捉窗口

  只需用鼠标选择你要捕捉的窗口。Shutter会以一种吸引人的、有用的方式突出显示当前选择的窗口。甚至可以简单地从列表中选择一个窗口，并以某种方式捕获它。

- 捕获菜单或工具提示

  用Shutter捕捉菜单或工具提示是非常容易的。你选择其中一个选项，一个（用户定义的）倒计时就开始了。在这段时间里，你可以打开所需的菜单或让一个特定的工具提示出现。Shutter会识别并捕获它。

- 捕获网站

  Shutter使用 gnome-web-photo 来捕获一个网站，而无需打开浏览器窗口

  ### 编辑

  尤其是当你为编写教程或手册而拍摄屏幕截图时，你需要对图片进行编辑，例如突出显示其中的某些部分。有了Shutter，你就不需要打开像GIMP这样的外部图形编辑器了，因为Shutter有自己的内置编辑器。以下是一些最重要的功能：

- 添加文本、箭头、矩形、椭圆......。

    内置编辑器允许你为你的截图添加基元（如矩形、直线等）、箭头或文本。每个形状都可以通过改变颜色、字体和/或线宽来定制。
    
- 审查/像素化以隐藏私人数据
  
    不想显示IP或电子邮件地址等敏感数据？Shutter为你提供了两个简单而有效的工具来隐藏这些数据。

- 自动增加形状
    在编写分步指南时，人们经常会在屏幕截图中添加递增的数字（通常是通过文字）。Shutter提供了一个特定的自动递增形状，可以添加到截图中。这再简单不过了!

- 裁剪

    内置的编辑器还包括裁剪屏幕截图的工具。只需用鼠标选择一个区域，或者在输入框中输入所需的尺寸。

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

> TBD: Unable to locate package gnome-web-photo 最近报错无法安装

## 设置

### 图片导出格式

打开 shutter，菜单中点 "首选项" --> "主要"。

图片格式中，默认时png格式，文件大小会稍微嫌大，可以设置为 jpg 格式，然后图片质量设置为 80%.

## 截图

### 快捷键截图

参考：https://shutter-project.org/faq-help/set-shutter-as-the-default-screenshot-tool

*System* *Settings* => Keyboard => shortcuts => custom shortcuts => add custom shortcuts

Name 设置为 shutter, command 设置为 `shutter -s`，然后设置快捷键，比如 `print screem` 键。

在按下截图快捷键，如我们上面设置的 `print screem` 键后，再点一下鼠标左键，就可以开始截图了。

- 选择截图区域： 按住鼠标左键拖动矩形区域，适当调整大小和位置，回车确认
- 放大/缩小：用鼠标滚轮对鼠标所在位置附近的屏幕进行放大/缩小

### 界面截图

在打开 shutter 界面后，通过界面上的按钮也可以方便的截图：

- selection：选择截图区域
- Desktop： 选择要截图的桌面，直接点是截取 workspace1 下的所有屏幕，也可以选择其他 workspace。多屏时如果只想截取一个屏幕，可以勾选 "Limit to current Monitor"，但我测试下来只能截取三个屏幕中中间的一个（主屏幕）。发现另外一个方便的方法，就是选windows时，点击在屏幕上没有任何窗口的地方。
- Windows：选择要截图的窗口，直接在下列框中选择有时会报错，比较方便的方式是点击Windows按钮后，再去点击要截图的窗口。

可以参考官方的截图教学视频：

https://shutter-project.org/screenshots/screencasts/
