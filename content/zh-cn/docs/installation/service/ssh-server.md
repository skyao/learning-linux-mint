---
title: "安装配置SSH服务器端"
linkTitle: "SSH服务器"
weight: 231
date: 2021-08-26
description: >
  在linux mint上安装SSH服务器
---

### 安装SSH

直接apt安装，然后设置数据所在的路径。

```bash
sudo apt-get install ssh
```

安装完成之后会启动，并注册为service，以后每次开机都能自动启动，可以通过 `service ssh status` 命令查看当前状态：

```bash
$ sudo service ssh status
● ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/lib/systemd/system/ssh.service; enabled; vendor preset: enabled)
     Active: active (running) since Tue 2021-08-31 03:46:10 CST; 7h left
       Docs: man:sshd(8)
             man:sshd_config(5)
    Process: 1192 ExecStartPre=/usr/sbin/sshd -t (code=exited, status=0/SUCCESS)
   Main PID: 1226 (sshd)
      Tasks: 1 (limit: 38038)
     Memory: 2.3M
     CGroup: /system.slice/ssh.service
             └─1226 sshd: /usr/sbin/sshd -D [listener] 0 of 10-100 startups

8月 31 03:46:10 skywork systemd[1]: Starting OpenBSD Secure Shell server...
8月 31 03:46:10 skywork sshd[1226]: Server listening on 0.0.0.0 port 22.
8月 31 03:46:10 skywork sshd[1226]: Server listening on :: port 22.
8月 31 03:46:10 skywork systemd[1]: Started OpenBSD Secure Shell server.
```

### 开启防火墙

通过 ssh 命令登录，如果能登录成功，则 `service ssh status` 命令可以看到最新的登录情况：

```bash
$ sudo service ssh status
......
8月 30 19:53:15 skywork sshd[3127]: Accepted password for sky from 192.168.0.41 port 38994 ssh2
8月 30 19:53:15 skywork sshd[3127]: pam_unix(sshd:session): session opened for user sky by (uid=0)
```

如果 ssh 命令被挂住，没有相应，则通常是因为ssh所在服务器上的防火墙开启并阻止了对22端口的访问。

`ufw statue` 命令可以看到当前防火墙的状态：

```bash
$ sudo ufw status
状态： 激活
```

可以先简单的关闭防火墙进行验证:

```bash
$ sudo ufw disable
在系统启动时启用和激活防火墙
```

如果可以正常ssh登录，说明只是防火墙的问题。

也可以通过linux mint自带的防火墙应用在图形化界面上进行操作。可以设置状态为是否开启，以及在开启时通过增加Rule来容许22端口对外暴露。







