---
title: "AdsPower Browser"
linkTitle: "AdsPower"
weight: 30
date: 2021-01-18
description: >
  AdsPower 指纹浏览器
---

## 介绍

https://www.adspower.com/antidetect-browser

- 硬件级隔离防止浏览器指纹追踪

- 一键登录 100+个账户

- 适配不同的代理类型和服务

- Selenium/REST API 集成实现工作流自动化

- 基于角色的权限确保操作安全

了解反检测浏览器的工作原理：

反检测浏览器是一种专用工具，通过伪装数字指纹（Canvas、WebGL、字体）来安全地操作多个在线账户。它通过伪造浏览器参数并按配置文件隔离 Cookie/IP，防止 Facebook、TikTok 或 Amazon 等平台将账户关联起来。

与暴露可识别数据的普通浏览器不同，反检测工具会轮换设备指纹并模拟人类行为，以规避检测算法。这就能为电商、社交媒体或广告测试实现安全的多账户管理，而不会被封禁。

为什么要使用反检测浏览器？

反检测浏览器通过绕过会标记共享设备的平台追踪系统，防止账户被封禁。它们能为管理 100 多个配置文件的团队实现安全的多重登录，同时通过 REST API/RPA 自动化任务。

对于电商卖家，它们通过动态地理位置测试来避免 ASIN 封禁。营销人员则用它们并行运行多个广告账户，而不会触发安全锁定。

至关重要的是，它们能在 VPN 或代理失效的地方提供指纹匿名性——这使它们成为安全扩展在线运营的必备工具。

AdsPower 不仅仅是一款反指纹浏览器，它还提供具有无与伦比规模的一体化反检测解决方案：

- 安全配置文件隔离：硬件级指纹掩蔽，支持 GPU 渲染分离

- 自动化引擎：内置本地 API 和 RPA 模板，用于机器人工作流

- 团队协作：基于角色的权限管理，并配备活动审计日志

- 代理集成：住宅/移动/SOCKS5 IP 自动轮换

## 下载

https://www.adspower.com/download

下载 linux 版本

## 安装

下载下来的 deb 直接安装即可。

## 配置

### 设置代理

左边导航栏 Proxies 中，点 Add Proxy，输入框中填写 "socks5://127.0.0.1:7897"，保存，会自动识别。

### 新建 profile

新建一个 profile，免费版本只能有两个 profile，好在凑合也够用了。

Browser Profile 中设置：

- Browser： 选择 Chrome 153

- OS： 选择 windows（备注：发现就算选择了 windows11,也会自动变回来 all windows，不清楚为什么）

- Proxy settings中选择 Saved proxy，然后 select proxy 中选择之前保存好的代理如 "socks5://127.0.0.1:7897"。可以点旁边的 check proxy 按钮进行测试。

Fingerprint 的设置中：

- WebRTC： 选择 Replace，只有这样 WebRTC 才能显示为美国住宅IP而不是中国大陆。

- Timezone： Based on IP

- Location： Based on IP

- Language： custom，然后用默认的 English （United Status）

- 其他保持默认


