# Nvidia显卡驱动安装

## 驱动安装

"开始菜单" -> "系统管理" -> "驱动管理器"，

Linux Mint 会先做一次系统更新检查，然后给出可以安装的驱动列表。

只要简单选择需要的驱动版本，然后安装即可，如下图：

![](images/drivers.jpg)

### 笔记本节能设置

为了节能，在右下角找到 nvidia 的图标，设置中找到 ”select the gpu you would like to use”，默认时NVIDIA，修改为 Intel，这样平时用 Intel 集显比较节能省电噪音低。

然后，在需要用到 nvidia 独立显卡时，可以再改回来。坦言，好像基本用不上...

### 最新375版本的BUG

最近在安装 nvidia 最新版本的 nvidia-375 驱动时，遇到报错：

```bash
/sbin/ldconfig.real: /usr/lib/nvidia-375/libEGL.so.1 is not a symbolic link
/sbin/ldconfig.real: /usr/lib32/nvidia-375/libEGL.so.1 is not a symbolic link
```

google 发现其他人也遇到类似问题：

- [libEGL.so.1 is not a symbolic link](https://askubuntu.com/questions/900285/libegl-so-1-is-not-a-symbolic-link)
- [/sbin/ldconfig.real: /usr/lib/nvidia-375/libEGL.so.1 is not a symbolic link
](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-375/+bug/1662860)

解决方法如下：

```bash
sudo mv /usr/lib/nvidia-375/libEGL.so.1 /usr/lib/nvidia-375/libEGL.so.1.org
sudo mv /usr/lib32/nvidia-375/libEGL.so.1 /usr/lib32/nvidia-375/libEGL.so.1.org
sudo ln -s /usr/lib/nvidia-375/libEGL.so.375.39 /usr/lib/nvidia-375/libEGL.so.1
sudo ln -s /usr/lib32/nvidia-375/libEGL.so.375.39 /usr/lib32/nvidia-375/libEGL.so.1
```

特别提醒， 特别提醒， 特别提醒：

上面的ln 命令，`/usr/lib32/nvidia-375/libEGL.so.375.39` 一定不能简单照抄，一定要和当前实际安装的驱动版本一致，也就是 libEGL.so.×××.×× 这个文件是和版本关联的，ln 时请务必注意。

不然 ln 到一个不存在的文件，驱动就会无法加载，启动时会黑屏无法进入操作系统。

如果不小心已经改错了无法进入，可以用安装盘启动，然后修改这个 ln 文件的地址，重启即可。



