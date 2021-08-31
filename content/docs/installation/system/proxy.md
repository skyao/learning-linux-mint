---
title: "网络代理快捷命令"
linkTitle: "网络代理"
weight: 227
date: 2021-08-30
description: >
  设置启用网络代理的快捷命令，方便随时开启和关闭网络代理
---

将以下内容添加到 .zshrc :


```properties
#proxy enable
alias proxyon='export all_proxy=socks5://192.168.0.1:23456;export http_proxy=http://192.168.0.1:3333;export https_proxy=http://192.168.0.1:3333'
alias proxyoff='unset all_proxy http_proxy https_proxy'
```

> 背景：我的代理安装在路由器上，http端口为 3333， socks5 端口为 23456