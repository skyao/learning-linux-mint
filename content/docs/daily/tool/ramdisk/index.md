---
title: "创建Ramdisk"
linkTitle: "Ramdisk"
weight: 424
date: 2021-08-26
description: >
  在ubuntu下创建ramdisk
---

### 创建ramdisk

```bash
cd ~/data/samba
mkdir ramdisk
chmod 777 ramdisk

sudo mount -t tmpfs -o size=16g ramdisk /home/sky/data/samba/ramdisk
```

### 测试ramdisk

在 ramdisk 被 mount 之后，可以用dd命令进行测试 

```bash
# 测试写入ramdisk
sudo dd if=/dev/zero of=/home/sky/data/samba/ramdisk/zero bs=4k count=100000

记录了1000000+0 的读入
记录了1000000+0 的写出
4096000000字节（4.1 GB，3.8 GiB）已复制，1.55497 s，2.6 GB/s

# 测试读取ramdisk
sudo dd if=/home/sky/data/samba/ramdisk/zero of=/dev/null bs=4k count=1000000
记录了1000000+0 的读入
记录了1000000+0 的写出
4096000000字节（4.1 GB，3.8 GiB）已复制，1.13431 s，3.6 GB/s
```

### 销毁ramdisk

```
sudo umount /home/sky/data/samba/ramdisk
```

### 参考资料

- [How to Easily Create RAM Disk on Debian, Ubuntu, Linux Mint, CentOS](https://www.linuxbabe.com/command-line/create-ramdisk-linux) 