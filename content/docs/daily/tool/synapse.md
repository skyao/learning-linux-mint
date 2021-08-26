---
title: "应用程序启动器Synapse"
linkTitle: "Synapse"
weight: 421
date: 2021-08-26
description: >
  Synapse是一个很轻巧的应用程序启动器。
---

{{% pageinfo color="primary" %}}
用来替代gnome-do
{{% /pageinfo %}}

## 介绍

ubuntu 20.04 之后就不再支持 gnome-do，取而代之的是 Synapse，功能和界面都差不多。

https://launchpad.net/synapse-project

## 安装

```
sudo apt install synapse
```

## 配置

首选项中设置：

1. 登录时启动
2. 取消勾选"显示通知区域图标"：没必要
3. 激活快捷键设置为 gnome-do 时代我习惯的 `alt + g`

插件中过了一遍，把用不倒的关了。

发现缺少一些必须的插件：

- Microsoft Edge：这是我现在主力浏览器
