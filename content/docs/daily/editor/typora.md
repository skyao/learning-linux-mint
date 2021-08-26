---
title: "Typora"
linkTitle: "Typora"
weight: 413
date: 2021-08-26
description: >
  非常漂亮的一个markdown编辑器，多平台通用
---

非常漂亮的一个markdown编辑器，和haroopad的左右两栏不同，typora是直接在一个界面中进行编辑和渲染。

我选择 typera 的理由： 1. 好用 2. 同时支持windows/linux/macos 三大平台

## 安装方式

https://typora.io/

安装方式：

```bash
wget -qO - https://typora.io/linux/public-key.asc | sudo apt-key add -
sudo add-apt-repository 'deb https://typora.io/linux ./'
sudo apt-get update
sudo apt-get install typora
```

### 跳过某个版本

使用时发现，原本正常的typora在升级到新版本之后就不能正常使用了，工具栏无法使用。反复卸载安装并清理本地缓存无效，最后只好跳过这个最新版本。

先看有哪些版本可选：

```bash
apt-cache madison typora
    typora |   0.11.6-1 | https://typora.io/linux ./ Packages
    typora |   0.11.2-1 | https://typora.io/linux ./ Packages
    typora |  0.10.11-1 | https://typora.io/linux ./ Packages
    typora |   0.9.98-1 | https://typora.io/linux ./ Packages
```

出问题的是最新的 0.11.6-1 版本，因此选择安装 0.11.2-1：

```bash
sudo apt install typora=0.11.2-1
```

然后就恢复正常了。

参考:

- [Ubuntu通过apt-get安装指定版本和查询指定软件有多少个版本](https://www.cnblogs.com/EasonJim/p/7144017.html)

## 配置

Linux 下 typora 的字体不是太好看，感觉是用主体设置的字体，而不能通过系统或者typora来设置。

这意味着如果要修改字体，则需要去修改主题文件。

TODO： 稍后研究
