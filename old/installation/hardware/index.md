# 硬件配置

tags: 驱动

安装完成之后，需要做必要的硬件配置。

## 功能设置

### 触摸板

"开始菜单" -> "系统设置" -> "鼠标和触摸板"，点 "触摸板"，开启 “打字时禁用触摸板”。实在不能忍受打字时不小心碰到触摸板,然后光标跑不知道哪里去了的感觉......

但是，随即发现打字时还是容易被触摸板影响，最后只好选择关闭触摸板。

## 硬件设置

### exfat支持

移动硬盘一般用的文件格式exfat，mint linux 18 之前的版本 默认不支持，需要安装 exfat-fuse / exfat-utils:

```bash
sudo apt-get install exfat-fuse exfat-utils
```

重启后生效。

对于 linux mint 18，默认已经提供了对exfat的支持，不再需要自己安装。

### 自动装载windows分区

linux mint 安装之后自带了ntfs-3g, 天然支持ntfs格式。

"开始菜单" -> "首选项" -> "开机自启动程序"，在开机自启动程序中增加开机自动装载windows分区的命令:

```bash
udisksctl mount -p block_devices/sdb4
```

具体有哪些分区可供装载，可以通过在命令行中输入 `udisksctl mount -p block_devices/` 然后双击 Tab 键列出来，如下图：

![](images/list_ntfs.jpg)

开机自启动设置如下：

![](images/auto_mount_ntfs.jpg)

### 关闭蓝牙设备

如果不需要使用蓝牙设备，可以打开 "开始菜单" -> "系统设置" -> "硬件" -> "蓝牙"，关闭对蓝牙的支持：

![](images/blueteeth_close.jpg)

注意： 建议去除显示托盘图标的勾选。



