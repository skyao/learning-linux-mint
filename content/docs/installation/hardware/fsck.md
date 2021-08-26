---
title: "启动时进行fsck硬盘检查"
linkTitle: "fsck硬盘检查"
weight: 215
date: 2021-08-26
description: >
  介绍Linux Mint下进行fsck硬盘检查的方式
---


如果遇到硬盘故障，linux mint 会在发生错误时，将系统所在盘符 mount 为 ro 只读，导致重启时无法进入操作系统。

这样开机只能进入内存虚拟的一个命令行界面，此时可以使用 fsck 命令扫描磁盘分区并尝试修复磁盘错误。

执行命令:

```bash
fsck -a /dev/sda*
```

如果无法自动修复问题，会要求手工修复，需要执行：

```bash
fsck /dev/sda*
```

然后一路确认即可。

