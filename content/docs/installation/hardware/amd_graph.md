---
title: "AMD显卡驱动安装"
linkTitle: "AMD显卡"
weight: 212
date: 2021-08-26
description: >
  介绍Linux Mint下AMD显卡的驱动安装
---

## 最新显卡

以 amd rx6800xt为例，AMD 的 linux 驱动非常更新及时，可以很好的支持最新的显卡。

在amd官方的支持页面

https://www.amd.com/en/support

选择 "Graphics" --> "AMD Redeon 6000 Series"  一路选择型号，然后点击"提交"。在结果中选择 "Ubuntu x86 64-Bit":

> Radeon™ Software for Linux® installer version 21.40.1 for Ubuntu 20.04.3

和以前的二进制安装文件不同，新版本的下载页面现在下载的只是一个驱动安装软件（installer），而不是驱动本身。

```bash
sudo apt install linux-image-5.4.0-94-generic linux-headers-5.4.0-94-generic linux-modules-extra-5.4.0-94-generic
```



下载得到 `amdgpu-install_21.40.1.40501-1_all.deb` ，安装方式：

```bash
sudo apt-get install ./amdgpu-install_21.40.1.40501-1_all.deb
```

之后，执行

```bash
sudo amdgpu-install --opencl=rocr --vulkan=amdvlk -y --accept-eula
```

开始安装，下载速度超级慢。

参考：https://amdgpu-install.readthedocs.io/en/latest/install-script.html#script-types

## 老显卡

以 amd r5 240 1G 为例，这样的十年前的老显卡已经找到不到最新 ubuntu release 的驱动了。比如这个卡的最新版本也只是2015年的，只支持到 ubuntu 15.12。

![](images/legacy-amd-driver-download.jpg)

不过，linux mint 自带了这些老显卡的驱动，虽不清楚这些驱动的版本和能力，但考虑到本来就是作为良机卡，足够了。

{{% pageinfo color="warning" %}}
注意：千万不要用上面的最新显卡驱动进行安装！

问题：安装过程会顺利完成，重启之后不仅仅新驱动无法启用，连原来自带的驱动也无法使用。

解决方式：通过上面的安装包，执行 `sudo ./amdgpu-uninstall` 卸载最新驱动，重启之后恢复自带驱动。
{{% /pageinfo %}}