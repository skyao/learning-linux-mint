---
title: "Audacious"
linkTitle: "Audacious"
weight: 30
date: 2021-08-26
description: >
  Audacious
---

## 介绍

http://audacious-media-player.org/

可惜，没有找到播放 DSD 格式的方法...

## 安装

audacious 默认存在于 ubuntu/linux mint 的仓库中，不过版本不是最新的。

audacious 官方首页有如下说明：

> Note that the versions of Audacious available in Debian stable and Ubuntu LTS releases tend to be rather out of date. Panda Jim of ubuntuhandbook.org maintains a PPA with newer versions for Ubuntu users.
>
> 请注意，Debian 稳定版和 Ubuntu LTS 版本中的 Audacious 版本往往已经过时。ubuntuhandbook.org的熊猫吉姆为Ubuntu用户维护了一个包含较新版本的PPA。

因此为了安装到最新的版本，需要添加下面的 PPA ，然后再 apt 安装。

```bash
sudo add-apt-repository ppa:ubuntuhandbook1/apps
sudo apt update
sudo apt-get install audacious
```

## 使用

界面也太朴素了点。