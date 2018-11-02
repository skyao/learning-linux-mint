---
date: 2018-10-27T15:05:00+08:00
title: 字体设置
menu:
  main:
    parent: "installation-system"
weight: 123
description : "修改Linux Mint的字体设置"
---

### 使用微软雅黑字体

备注：非视网膜屏幕推荐。

1. 从win10系统中提取出字体文件  msyh.ttf 和 msyhbd.ttf

2. 在linux mint 系统字体文件夹中建立对应的字体文件夹

    ```bash
    sudo mkdir /usr/share/fonts/msyh
    sudo cp msyh.ttf msyhbd.ttf   /usr/share/fonts/msyh
    sudo fc-cache  -fv
    ```

3. `菜单-->首选项-->字体` 设置字体

高清屏幕（2k/3k/4k）推荐下面的文泉微米字体。

### 修改字体为文泉微米等宽黑

打开菜单-->首选项-->字体，一律修改成文泉驿等宽微米黑，字体大小也适当加大。

这个方式会比默认风格要好看一些。

### 移除不需要的字体

有些地方的字体会继续保留为楷体，需要在软件管理器中，找到"Fonts-arphic-ukai"和"Fonts-arphic-uming"，移除这两个字体。

重新启动后，可以发现原来的一些自体比如命令行下的楷体（默认，超级丑）就变为前面设置的文泉微米等宽黑了。

### 设置命令行窗口自体

打开命令行，"编辑" -> "首选项" 中勾选自定义自体，适当放大字体，默认12,可以考虑20。
