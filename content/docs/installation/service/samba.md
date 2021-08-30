---
title: "安装配置Samba文件共享"
linkTitle: "Samba文件共享"
weight: 232
date: 2021-08-26
description: >
  在linux mint上安装Samba，进行文件共享
---

### 安装samba

直接apt安装，然后设置数据所在的路径。

```bash
sudo apt-get install samba

cd
mkdir -p data/samba
chmod 777 data/samba
```

### 配置samba

`sudo vi /etc/samba/smb.conf` 打开配置文件，在文件末尾添加以下内容：

```properties
[share]
path = /home/sky/data/samba
valid users = sky
writable = yes
```

创建samba用户:

```bash
sudo smbpasswd -a sky
```

重启samba服务

```bash
sudo service smbd restart
```

### 访问samba

在其他linux机器上使用地址 `smb://172.168.0.10` 访问，在windows下使用地址 `\\172.0.0.10`。

### 参考资料

- [Ubuntu 20 开启samba文件共享](https://blog.csdn.net/dslobo/article/details/108175737)
- [samba升级_Ubuntu20.04升级后共享文件打不开处理方法](https://blog.csdn.net/weixin_39549899/article/details/110996857?utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7EBlogCommendFromMachineLearnPai2%7Edefault-1.base&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7EBlogCommendFromMachineLearnPai2%7Edefault-1.base) : 如果遇到samba版本问题导致的不能访问，可以参考这个文章



