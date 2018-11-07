---
date: 2018-11-07T13:05:00+08:00
title: polipo
menu:
  main:
    parent: "daily-network"
weight: 349
description : "polipo"
---

shadowsock 是 socks5 的代理，有些程序对 socks5 的支持不好，此时需要提供额外的 http 代理。

因此我们引入 polipo，在 shadowsock 提供的 socks5 代理的基础上提供 http 代理。

## 安装

```bash
sudo apt-get install polipo
```

然后打开配置文件 `/etc/polipo/config`, 设置 ParentProxy 为 Shadowsocks:

```bash
socksParentProxy = "localhost:11080"
socksProxyType = socks5
proxyAddress = "0.0.0.0"
```

注意：如果不设置proxyAddress，则默认为127.0.0.1，这样会导致不能通过具体的IP地址做代理，对于某些程序，比如虚拟机中的程序，就无法使用．为此设置为"0.0.0.0"这样会监听所有IP地址．

参考资料: https://www.irif.fr/~jch/software/polipo/polipo.html

保存配置修改之后重启 polipo:

```bash
sudo service polipo restart
```

## 使用

之后执行命令时加入 `http_proxy=http://localhost:8123` 如 `http_proxy=http://localhost:8123 curl ip.gs` 即可。

为了方便，可以有两种优化方式：

1. 加别名

	在 `/etc/profile` 中增加下列内容：

	```bash
    alias hp="http_proxy=http://localhost:8123"
   ```

	需要时在命令前加 `hp` 即可，如 `hp curl ip.gs`。

2. 直接export

	如果觉得每次都加hp前缀麻烦，可以在 `/etc/profile` 中增加下列内容：

	```bash
    export http_proxy=http://localhost:8123
   ```


