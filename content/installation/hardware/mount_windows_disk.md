---
date: 2018-10-27T14:30:00+08:00
title: 挂载Windows盘符
menu:
  main:
    parent: "installation-hardware"
weight: 114
description : "介绍Linux Mint下挂载Windows盘符的方式"
---

安装linux、windows双操作系统时，可以在linux下直接挂载windows的盘符，这样可以访问windows下的文件系统，非常方便。

新版本的ubuntu16.04、Linux mint 18都已经内置了ntfs的支持，只需要简单挂载就好。最方便的方式是在开机时自动挂载。

### 设置开机自动挂载

在开机自启动程序中，增加一个开机启动项，命令为：

```bash
udisksctl mount -p block_devices/nvme0n1p4
```

![](images/auto_mount_ntfs.jpg)

### 解决无法装载的问题

如果windows在关机时进行了休眠，则无法装载，报错如下：

```bash
Error mounting /dev/nvme0n1p4 at /media/sky/win10: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/nvme0n1p4" "/media/sky/win10"' exited with non-zero exit status 14: Windows is hibernated, refused to mount.
Failed to mount '/dev/nvme0n1p4': 不允许的操作
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
```

解决这个问题的最好方式是消除休眠状态。一般重新启动到windows下，然后再次重启进linux，就OK。

前提是已经关闭了windows的快速启动功能，不然还会继续报同样错误。关闭快速启动的办法是进入windows，在控制面板 -> 电源管理中，选择关闭盖子的功能，点击"不能更改的选项"，去掉快速启动的勾选。

但偶尔还是会遇到即使上面的事情都做好了，依然还是继续报错说"Windows is hibernated"。

此时需要想办法删除windows盘符上的休眠文件`hiberfil.sys`，具体作法是在linux中执行命令：

```bash
sudo mkdir /media/sky/win10
sudo ntfs-3g -o remove_hiberfile /dev/nvme0n1p4 /media/sky/win10
```

最恶劣的情况是，windows在即使关闭快速启动功能的情况下也还是会继续生成休眠文件，非常不可理喻。解决的方式是彻底关闭windows的休眠功能。以管理员权限启动命令行，执行命令：

```bash
powercfg /h off
```

### 参考资料

- [How to Do a Full Shutdown in Windows 8 Without Disabling Hybrid Boot](https://www.howtogeek.com/129021/how-to-do-a-full-shutdown-in-windows-8-without-disabling-hybrid-boot/)
- [How to mount Windows (NTFS) filesystem due to hibernation](https://wiki.manjaro.org/How_to_mount_Windows_(NTFS)_filesystem_due_to_hibernation): 这篇讲的很详细

