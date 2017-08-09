# snap

## 介绍

snap 是通用的 Linux 包管理程序。

- https://www.ubuntu.com/desktop/snappy
- https://snapcraft.io/docs/core/usage
- [command reference](https://snapcraft.io/docs/reference/snap-command)

## 安装

按照 snapcraft 的说法，ubuntu 16.04 默认安装了 snap：

https://snapcraft.io/docs/core/install-ubuntu

但是我们会发现 linux mint 18.1 默认**没有**安装snap，原因不明，因此需要自己动手安装snap。

### 错误安装方式

**警告！**

不能按照标准的 ubuntu 16.04 安装方式来安装，如果照做的话：

```bash
sudo apt update
sudo apt install snapd
```

安装完成之后可以看到snap版本信息为：

```bash
snap --version
snap       2.25
snapd      2.26.14
series     16
linuxmint  18
kernel     4.4.0-87-generic
```

snap 会在之后安装其他模块时报错:

```bash
snap install core
error: cannot perform the following tasks:
- Setup snap "core" (2462) security profiles (cannot setup seccomp for snap "core": fork/exec /usr/lib/snapd/snap-seccomp: no such file or directory)
- Setup snap "core" (2462) security profiles (fork/exec /usr/lib/snapd/snap-seccomp: no such file or directory)
```

导致 snap 完全无法使用。

### 正确安装方式

正确的安装方法是:

```bash
sudo -i
add-apt-repository ppa:snappy-dev/edge -y
apt update
# If you already had snapd installed you need to do a dist-upgrade
apt dist-upgrade
# If not, install it with this:
hp apt install snapd ubuntu-core-launcher
```

> 注: hp 是设置 http_proxy 的alias。见前面代理设置的章节

此时看snap安装的版本信息，版本和前面的不同，

```bash
snap --version
snap       2.27~rc8+git304.b976c11~ubuntu16.04.1
snapd      2.27~rc8+git304.b976c11~ubuntu16.04.1
series     16
linuxmint  18
kernel     4.4.0-87-generic
```

此时可以正常安装　core 模块:

```bash
hp snap install core
2017-08-10T01:23:24+08:00 INFO Waiting for restart...
core 16-2.26.14 from 'canonical' installed
```
