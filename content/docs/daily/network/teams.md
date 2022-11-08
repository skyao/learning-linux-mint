---
title: "Teams"
linkTitle: "Teams"
weight: 447
date: 2021-08-26
description: >
  安装微软Teams
---



## 下载安装

Teams 有支持 ubuntu 的preview 版本，直接下载 deb 文件安装即可

https://www.microsoft.com/en-us/microsoft-teams/download-app

Linux DEB (64-bit) 

## 登录微软帐号

比较麻烦的在 ubuntu 上登录微软的帐号。

### 安装 intune app

参考文档为：

https://learn.microsoft.com/en-us/mem/intune/user-help/microsoft-intune-app-linux

准备完成之后，执行：

```bash
$ sudo apt install intune-portal
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 intune-portal : Depends: libssl1.1 (>= 1.1.0) but it is not installable
                 Depends: msalsdk-dbusclient (>= 1.0) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

缺少依赖包，libssl1.1 可以从这里下载：

https://packages.ubuntu.com/bionic/amd64/libssl1.1/download

msalsdk-dbusclient 安装时发现还缺少依赖包：

```bash
sudo apt install msalsdk-dbusclient

The following packages have unmet dependencies:
 msalsdk-dbusclient : Depends: libsdbus-c++0 (>= 0.8.3) but it is not installable
```

 libsdbus-c++0 ，可以从下面的页面下载 64-bit deb package 安装：

https://www.ubuntuupdates.org/package/core/focal/universe/backports/libsdbus-c%2B%2B0

再次安装 msalsdk-dbusclient：

```bash
$ sudo apt install msalsdk-dbusclient

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  microsoft-identity-broker microsoft-identity-diagnostics
The following NEW packages will be installed:
  microsoft-identity-broker microsoft-identity-diagnostics msalsdk-dbusclient
0 upgraded, 3 newly installed, 0 to remove and 3 not upgraded.
......
Setting up msalsdk-dbusclient (1.0.1) ...
Processing triggers for dbus (1.12.20-2ubuntu4.1) ...
Processing triggers for libc-bin (2.35-0ubuntu3.1) ...
```

### 启动 intune

按照要求：

https://learn.microsoft.com/en-us/mem/intune/user-help/enroll-device-linux

遇到问题： 在 intune 登录时，输入用户名（微软邮箱）后，直接报错：

```
Terms of User Error

We couldn't sign you in. Please try again, or contact your administrator.
```

无法解决，只能放弃。

