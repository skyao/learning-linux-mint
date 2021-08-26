---
title: "AMD显卡驱动安装"
linkTitle: "AMD显卡"
weight: 212
date: 2021-08-26
description: >
  介绍Linux Mint下AMD显卡的驱动安装
---

使用 amd rx580 显卡在 19.3 版本下安装驱动，更新于 2020年3月底。写代码还是喜欢linux系统，捣鼓了一整子黑苹果，又回到linux mint的怀抱了。

背景：操作系统安装完成之后，默认已经安装好amd 显卡驱动，不过总感觉有点不对，手工再安装一边。

官方下载网站：

https://www.amd.com/zh-hans/support

选择型号，跳转到下载页面，选择 “ Ubuntu x86 64 位 ”， Radeon™ Software for Linux® Driver for Ubuntu 18.04.3

- Revision Number：19.50
- File Size：308 MB
- 发布日期：2019年12月19日

下载之后，解压缩，进入目录，执行命令：

```bash
./amdgpu-pro-install

# 如果遇到报错说驱动已经安装，执行下面命令先删除现有版本再安装
# /usr/bin/amdgpu-pro-uninstall 

安装到最后，有个警告，看来是内核太新
WARNING: amdgpu dkms failed for running kernel

```

" amdgpu dkms failed for running kernel" 这是关键

- https://community.amd.com/thread/248166： 这个问题很多人遇到了，根本原因在于这个版本对 linux 5.0以上内核不支持。
- https://www.amd.com/en/support/kb/release-notes/rn-rad-lin-20-10-early-preview： 这个是新版本的驱动，支持 linux 5.0 内核，不过还是一个早期预览版本。
- https://amdgpu-install.readthedocs.io/en/latest/install-installing.html： 安装文档，没细看，直接 `./amdgpu-pro-install` 搞定就不去研究了。

最后的结果：这个 20.10 早期预览版本在 linut mint 19.3 (基于18.04.1版本的Ubuntu) + 5.3.0-42-generic 内核（2020年3月底最新版本）上顺利安装成功。

--------------------------------------

以下内容已经过期。

备注1：这是Linux Mint18下的记录，Linux Mint 19下我还有没有使用过AMD显卡。

备注2： AMD 的linux 驱动支持烂的要死，最好别用 AMD 的显卡！

## 下载

amd 驱动下载地址：

http://support.amd.com/zh-cn/download

选择产品和操作系统之后，对于linux系统，会跳转到下面的页面：

http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Driver-for-Linux-Release-Notes.aspx

在这里可以找到下载链接，不过下载速度非常的慢，而且百度云无法离线下载。

可以换下面的地址，这里虽然下载也慢，但是可以用百度云先帮忙离线下载。

https://www.touslesdrivers.com/index.php?v_page=23&v_code=53718&v_langue=en

## 安装

下载完成后，安装方式可以参考下文：

http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx

步骤如下：

```bash
tar -Jxvf amdgpu-pro-17.10-429170.tar.xz
cd amdgpu-pro-17.10-429170
./amdgpu-pro-install -y
```

此时会报错，"Unsupported OS"：

```bash
Unsupported OS
```

打开 `amdgpu-pro-install`，找到 os_release() 函数：

```bash
function os_release() {
	......
	case "$ID" in
	ubuntu)
		PACKAGES="amdgpu-pro amdgpu-pro-lib32 amdgpu-pro-dkms"
		;;
	......
}
```

修改这个函数，将 "ubuntu)" 修改为 "linuxmint"，即:

```bash
function os_release() {
	......
	case "$ID" in
	linuxmint)
	......
}
```

修改之后继续安装即可。

为了确保当前使用的账号可以使用该 vulkan 驱动，需要将用户加入到 `video` group:

```bash
sudo usermod -a -G video $LOGNAME
```

## 升级内核

然后重启电脑。然后，启动不起来...... 经查找是 amdgpu-pro-17.10 驱动需要 4.8 版本的内核，而 linux mint 18.1 的内核版本是 4.4 。

解决方案：

1. 先卸载 amdgpu-pro-17.10 驱动
2. 升级系统内核至 4.8
3. 重新安装 amdgpu-pro-17.10 驱动

> 注： 没有找到 amdgpu-pro-17.10 驱动的卸载脚本，最后修改 `amdgpu-pro-install` 的最后一行，将 `amdgpu_pro_${0##*-} "$@"` 修改为 `amdgpu_pro_uninstall` 执行即可

最后补充： 当时折腾这个显卡驱动是因为 vmware 启动虚拟机时报错说驱动有问题，无法打开显卡的硬件支持。后来发现是 vmware 的配置问题，默认情况下 mint linux 的 amd 显卡驱动时可以用的，而且稳定。所以最后的结果，我把辛辛苦苦安装好的 amd 驱动又卸载了。



