---
title: "Conky"
linkTitle: "Conky"
weight: 311
date: 2021-08-26
description: >
  Conky 是一个轻量级的Linux系统监控工具，非常适合日常用来监控cpu，进程，内存和网络。
---

## 安装

新版本的conkey的安装和配置方式和之前的完全不一样了。

可以直接 apt-get 安装

```bash
sudo apt-get install conky-all
```

conky-manager 不再存在了。

安装完成之后执行 `conky &` 命令，就能看到 conky 的监控界面了。但，很丑很丑。

## 配置

暂时先不研究。



## 参考

参考这三个应该就可以的：

- [How to install Conky System Monitor on Ubuntu 20.04 LTS](https://www.how2shout.com/linux/how-to-install-conky-system-monitor-on-ubuntu-20-04-lts/) ： 安装
- [Conky system monitor- Widget to view Linux Process, CPU and Memory](https://www.how2shout.com/linux/conky-system-monitor-widget-to-view-linux-process-cpu-and-memory/)： 配置
- [](https://github.com/brndnmtthws/conky/wiki/Configs): 构建好了的主题
