---
title: "安装配置nfs文件共享"
linkTitle: "nfs文件共享"
weight: 233
date: 2021-08-26
description: >
  在linux mint上安装nfs，进行文件共享
---



## 配置nfs服务器端

### 安装nfs-server

```bash
sudo apt update
sudo apt install nfs-kernel-server

```

查看 nfs-server 的状态：

```bash
$ sudo systemctl status nfs-server

● nfs-server.service - NFS server and services
     Loaded: loaded (/lib/systemd/system/nfs-server.service; enabled; vendor pr>
     Active: active (exited) since Wed 2021-12-29 00:45:44 CST; 5min ago
   Main PID: 758742 (code=exited, status=0/SUCCESS)
      Tasks: 0 (limit: 154080)
     Memory: 0B
     CGroup: /system.slice/nfs-server.service

Dec 29 00:45:43 skyserver systemd[1]: Starting NFS server and services...
Dec 29 00:45:44 skyserver systemd[1]: Finished NFS server and services.
```

### 创建nfs共享目录

```bash
sudo mkdir /mnt/nfs-share
```

让所有的客户端都可以访问所有的文件，修改文件的所有者和许可：

```bash
sudo chown nobody:nogroup /mnt/nfs-share
sudo chmod -R 777 /mnt/nfs-share
```

### 授权客户端访问nfs server

`sudo vi /etc/exports` 打开文件，为每个客户端授权访问:

```bash
/mnt/nfs-share client-IP(rw,sync,no_subtree_check)
```

如果有多个客户端则需要重复多次授权，也可以通过子网掩码一次性授权：

```bash
/mnt/nfs-share 192.168.0.0/24(rw,sync,no_subtree_check)
```

参数解释：

- rw (Read and Write)
- sync (Write changes to disk before applying them)
- no_subtree_check (Avoid subtree checking )

执行下面命令进行export：

```bash
sudo exportfs -a
```

### 配置防火墙

关闭防火墙，或者设置防火墙规则:

```bash
sudo ufw allow from 192.168.0.0/24 to any port nfs
```

## 配置nfs客户端

### 安装nfs软件

```bash
sudo apt update
sudo apt install nfs-common
```

### 挂载nfs server到本地

创建用来挂载 nfs server的本地目录：

```bash
sudo mkdir -p /mnt/nfs-skyserver
```

挂载 nfs server 共享目录到这个客户端本地目录:

```bash
sudo mount 192.168.0.40:/mnt/nfs-share /mnt/nfs-skyserver
```

验证一下：

```bash
cd /mnt/nfs-skyserver 
touch a.txt
```

回到服务器端那边检查一下看文件是否创建。

### 设置永久挂载

上面的挂载在重启之后就会消失，`/mnt/nfs-skyserver` 会变成一个普通的目录。

为了在机器重启之后继续自动挂载, `sudo vi /etc/fstab` 打开文件增加以下内容:

```properties
# nfs from skyserver
192.168.0.40:/mnt/nfs-share /mnt/nfs-skyserver   nfs   defaults,timeo=900,retrans=5,_netdev	0 0
```







## 参考资料

- [How to Install NFS Server on Ubuntu 20.04 (Focal Fossa)](https://www.linuxtechi.com/install-nfs-server-on-ubuntu/)
- [How to Install and Configure an NFS Server on Ubuntu 20.04](https://linuxize.com/post/how-to-install-and-configure-an-nfs-server-on-ubuntu-20-04/)
