---
title: "Clash Verge"
linkTitle: "Clash Verge"
weight: 20
date: 2021-01-18
description: >
  Clash Verge翻墙软件
---

## 下载

最好是从 github 下载：

https://github.com/Clash-Verge-rev/clash-verge-rev/releases

官方的不是最新版本：

https://clash-meta.org/download/linux-deb/#download

## 安装

下载下来的 Clash.Verge_2.5.7_amd64.deb 直接安装即可。

## 配置

启动 Clash Verge，在界面左边的 Profile 下， import profile URL 或者点 NEW 创建新的 profile。

打开 "Settings" --> "system settings"，开启 Tun Mode，提示要安装 service 时选择同意。

Tun Mode 设置中，Tun Stack 要选择 System 而不是默认的 Gvisor （以支持 UDP 的 WebRTC）。Router Exclude Address 中添加要排除的地址如 "192.168.0.0/16"。

## chain proxy 配置

先要准备好美国的住宅IP代理。

### 添加 proxy

首先需要在现有的 Profile 里面增加一个 proxy，在当前 profile 上右键，选择 "Edit Proxy", 输入如下内容：

```bash
# 请替换为实际的用户名，密码，代理IP和端口
socks5://name:password@1.1.1.1:8888
```

点击 "Append proxy" 添加在最后。点击左边导航栏中的 "Proxies"，可以看到目前的代理列表，其中就会有一个代码显示为 "SOCKS5 xx.xx.xx.xx"。

### 配置 chain proxy 

点击左边导航栏中的 "Proxies"，右上角选择 "CHAIN PROXY"，然后先点击左边的一个普通代理，再点击上一步添加的美国住宅IP的代理。

proxy 默认使用 "Rule"，不要开 "Global"。

### 检测

在 chain proxy 配置好之后，再配置好 AdsPower 指纹浏览器，然后在正式启用之前先进行检测：

- https://ipleak.net/ 

- https://ipinfo.io/48.46.143.90

- https://scamalytics.com/ip/48.46.143.90

这几个都不够准确，主要还是看下面这个：

- https://www.browserscan.net/

尤其是 WebRTC，走的 UDP，容易出问题：

- IP：48.46.143.90(USA)
- WebRTC： 101.82.164.87(Chinese mainland)
- WebRTC STUN： 101.82.164.87(Chinese mainland)

