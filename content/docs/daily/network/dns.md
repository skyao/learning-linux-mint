---
title: "设置DNS"
linkTitle: "设置DNS"
weight: 446
date: 2021-08-26
description: >
  设置阿里的DNS，提高网络响应速度, 实测效果明显。
---


设置阿里的DNS，提高网络响应速度, 实测效果明显。

> 备注：下面的方法在ubuntu18.04、linux mint 19下无法使用。

### 做法

打开终端执行:

```bash
sudo vim /etc/resolvconf/resolv.conf.d/tail
```

添加下面两行Alidns：

```bash
nameserver 223.5.5.5
nameserver 223.6.6.6
```

保存后执行:

```bash
sudo resolvconf -u
```

查看 `/etc/resolv.conf` 可以看到多了上面两条 nameserver.