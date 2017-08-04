# AMD显卡驱动安装

总结： AMD 的linux 驱动支持烂的要死，最好别用 AMD 的显卡！

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




