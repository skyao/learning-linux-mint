---
title: "安装配置远程桌面连接服务"
linkTitle: "远程桌面连接"
weight: 233
date: 2021-08-26
description: >
  在linux mint上安装配置远程桌面连接服务
---

## XRDP

### 安装xrdp

安装 xrdp：

```bash
sudo apt install xrdp
```

命令输出如下：

```bash
sudo apt install xrdp

[sudo] sky 的密码：          
正在读取软件包列表... 完成
正在分析软件包的依赖关系树       
正在读取状态信息... 完成       
将会同时安装下列软件：
  xorgxrdp
建议安装：
  guacamole xrdp-pulseaudio-installer
下列【新】软件包将被安装：
  xorgxrdp xrdp
升级了 0 个软件包，新安装了 2 个软件包，要卸载 0 个软件包，有 15 个软件包未被升级。
需要下载 488 kB 的归档。
解压缩后会消耗 3,212 kB 的额外空间。
您希望继续执行吗？ [Y/n] Y
获取:1 http://mirrors.dgut.edu.cn/ubuntu focal/universe amd64 xrdp amd64 0.9.12-1 [428 kB]
获取:2 http://mirrors.dgut.edu.cn/ubuntu focal/universe amd64 xorgxrdp amd64 1:0.2.12-1 [59.9 kB]
已下载 488 kB，耗时 0秒 (1,180 kB/s)
正在选中未选择的软件包 xrdp。
(正在读取数据库 ... 系统当前共安装有 387220 个文件和目录。)
准备解压 .../xrdp_0.9.12-1_amd64.deb  ...
正在解压 xrdp (0.9.12-1) ...
正在选中未选择的软件包 xorgxrdp。
准备解压 .../xorgxrdp_1%3a0.2.12-1_amd64.deb  ...
正在解压 xorgxrdp (1:0.2.12-1) ...
正在设置 xrdp (0.9.12-1) ...

Generating 2048 bit rsa key...

ssl_gen_key_xrdp1 ok

saving to /etc/xrdp/rsakeys.ini

Created symlink /etc/systemd/system/multi-user.target.wants/xrdp-sesman.service → /lib/systemd/system/xrdp-sesman.service.
Created symlink /etc/systemd/system/multi-user.target.wants/xrdp.service → /lib/systemd/system/xrdp.service.
正在设置 xorgxrdp (1:0.2.12-1) ...
正在处理用于 systemd (245.4-4ubuntu3.11) 的触发器 ...
正在处理用于 man-db (2.9.1-1) 的触发器 ...
正在处理用于 libc-bin (2.31-0ubuntu9.2) 的触发器 ...
```

然后，有一件非常重要的事情，但很多很多教程和博客里面都没有说:

```bash
echo env -u SESSION_MANAGER -u DBUS_SESSION_BUS_ADDRESS cinnamon-session>~/.xsession
```

一定要有这个 .xsession 文件，而且内容是上面的内容，不是 `xfce4-session` 之类。否则就会出现连接成功之后黑屏然后立即断开的问题。

参考资料：

- [Using RDP With Linux Mint 20 Cinnamon](https://www.rootisgod.com/2020/Using-RDP-With-Linux-Mint-20-Cinnamon/)

### 使用体验

速度超级慢，简直抓狂，我这还是局域网千兆有线网卡直接连接。

### AnyDesk

https://anydesk.com/zhs/downloads/linux

试用了一下，速度很不错，图形显示效果尤佳。秒杀 xrdp ！

但可惜是商业付费产品。





