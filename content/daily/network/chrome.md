---
date: 2018-11-07T13:05:00+08:00
title: Chrome浏览器
draft: true
menu:
  main:
    parent: "daily-network"
weight: 347
description : "Google chrome 浏览器"
---

chrome 浏览器个人最喜欢的浏览器。

## 安装

在chrome官方下载适合的 amd 64位的 debian 版本，或者直接用这个下载链接下载最新版本:

https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb

然后直接用 `GDebi package installer` 安装即可。

## 插件

chrown 的webstore，可以从这里寻找和安装插件：

https://chrome.google.com/webstore/category/extensions?hl=zh-CN

### SwitchyOmega

在 google chrome webstore 中可以安装 SwitchyOmega 插件来方便的管理代理服务器(还是主要为了翻墙),然后加入场景设置使用本地 shadowsocks 作为代理服务器.

#### 安装SwitchyOmega

搜索 `SwitchyOmega` ，然后直接安装：

![](images/switchy_search.jpg)

但是，如果 google chrome webstore 被墙，就麻烦了。此时需要做的事情是：

1. 手工下载

	SwitchyOmega的备用下载地址： https://github.com/FelisCatus/SwitchyOmega/releases

2. 本地安装

	在Chrome的地址栏中输入 "chrome://extensions/" 打开扩展程序管理界面，然后拖放下载的 SwitchyOmega.crx 文件到这个界面，就可以安装了。

    注意不要直接拖放到普通页面，chrome在最新的版本中已经不再容许这种方式安装。

#### 配置shadowsocks

![](images/switchy_shadowsocks.jpg)

注意:代理协议一定要设置为 SOCKS5.

#### 设置自动切换

为了方便, SwitchyOmega 中设置自动切换,规则列表设置格式为 `AutoProxy`。

规则列表网址为下面地址,保存后更新:

https://raw.githubusercontent.com/gfwlist/gfwlist/master/gfwlist.txt

这样用 chrome 上网就可以自动切换代理,需要翻墙时自动连 shadowsocks,不需要时直连.

![](images/switchy_auto_switch.jpg)