---
title: "软件管理器"
linkTitle: "软件管理器"
weight: 70
date: 2026-08-26
description: >
  解决软件管理器打不开的问题
---

## 问题表现

新安装的 linux mint 22.3 版本，打开 software manager，一直转圈圈，提示 generating cache, one moment 。但等了很久也无法正常完成，感觉卡住了。

## 解决方法

```bash
pgrep -f mintinstall          # 拿到 PID
ss -tpn | grep -E "mintinstall|python3"   # 看它有没有挂着对外 TCP 连接
```

看到输出为：

```bash
4116
4119
ESTAB    0      0      [240e:46d:ac00:2a84:d082:c090:d662:e259]:47552      [2a04:4e42:68::347]:443  users:(("mintinstall",pid=4119,fd=30)) 
ESTAB    0      0      [240e:46d:ac00:2a84:d082:c090:d662:e259]:47564      [2a04:4e42:68::347]:443  users:(("mintinstall",pid=4119,fd=37)) 
```

2a04:4e42::/32 是 Fastly 的 CDN 段，也就是 dl.flathub.org（Flathub 的下载服务器）。mintinstall 生成缓存时，除了 apt，还会刷新 Flathub 的 appstream 元数据——它在后台通过 Flatpak 去拉 Flathub，而 Flathub 的国际线路（尤其还走 IPv6）在国内基本是"TCP 能连上、但 HTTP 数据半天流不动"，于是 mintinstall 就永远挂在那句 "Generating cache" 上。

目前我基本不用 Flatpak，所以简单点直接把 flathub 源摘掉：

```bash
sudo flatpak remote-delete --system flathub
```

重新启动 mintinstall，就好了：

```bash
pkill -f mintinstall
rm -rf ~/.cache/mintinstall
mintinstall
```

