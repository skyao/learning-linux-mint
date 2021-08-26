---
title: "取消PPA仓库"
linkTitle: "取消PPA仓库"
weight: 221
date: 2021-08-26
description: >
  取消PPA仓库以加速apt-get update的速度
---


### 取消PPA仓库

当添加太多的 PPA 仓库之后，apt update 的速度就会慢很多。

考虑到大多数软件不会经常更新，而且我们也没有立即更新的迫切需求，因此建议取消这些 PPA 仓库。

具体做法，"开始菜单" -> "系统管理" -> "软件源" -> "PPA", 将不需要及时更新的软件的 PPA 取消。

这个操作可以在每次你觉得 `apt-get update` 速度慢时检查 :)

