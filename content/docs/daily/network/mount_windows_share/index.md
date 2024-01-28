---
title: "挂载 windows 共享目录"
linkTitle: "挂载 windows 共享目录"
weight: 448
date: 2021-08-26
description: >
  为了方便使用 windows 共享的目录，最好能直接 mount 进来。
---


为了方便使用 windows 共享的目录，最好能直接 mount 进来。

## 安装

需要安装 `cifs-utils`：

```bash
apt-get install cifs-utils
```

## 挂载

使用 mount 命令装载：

```bash
sudo mkdir /mnt/nas/d
sudo mount -t cifs -o rw,username=sky,password=***,uid=1000,gid=1000 //192.168.0.30/d/ /mnt/nas/d
```

- username 和 password 是访问 windows 共享目录需要的账户密码
- rw 表示可以读写
- uid和gid 可以通过 id 命令看到，设置之后mount之后的目录就可以方便当前用户直接读写访问
- `//192.168.0.30/d/` 是 smb 的共享路径，可以通过 "smb://192.168.0.30/d/" 访问验证
- `/mnt/nas/d` 是装载的目标路径，必须事先存在，可以在 mount 之前先创建好

## 卸载

不需要使用时，可以 umount 卸载：

```bash
sudo umount /mnt/nas/d
```

## 改进脚本

为了方便使用，避免反复输入上面的 mount 命令，一个比较常见的做法是开机自动装载。但是考虑到我的笔记本是在公司和家里移动，而两边可以 mount 的东西不一样。另外也不是每次开机都需要 mount。

因此选择了自己准备脚本，需要时手工执行。另外不想 mount 到 `/mnt/` 下，也不想 mount 为 root 账号。

最后的解决方式是，我在自己的 home 目录下建立了一个 mount 子目录，然后将需要的 mount 和 umount 脚本扔进去。需要时执行对应 mount 脚本，就将 windows 共享目录 mount 到 `/home/myid/mount` 下，而且当前用户有读写权限，使用非常方便。

以 mount-nas.sh 为例，内容如下：

```bash
#!/bin/bash

CURRENT=`pwd`

# 我的 nas 是台普通windows电脑，共享了几个盘符
NAS_FOLDERS=("d" "m" "n" "p")

for nas_folder in ${NAS_FOLDERS[@]};do
	target_folder="$CURRENT/nas-$nas_folder"
	if [ ! -d "$target_folder" ]; then
		mkdir $target_folder
		echo "create folder: $target_folder"
	fi

	sudo mount -t cifs -o rw,username=sky,password=***,uid=1000,gid=1000 "//192.168.0.30/$nas_folder/" $target_folder
done

read -n1 -p "Press any key to exit..."
```

同时准备了一个 umount-nas.sh 脚本，方便卸载：

```bash
#!/bin/bash

CURRENT=`pwd`

NAS_FOLDERS=("d" "m" "n" "p")

for nas_folder in ${NAS_FOLDERS[@]};do
	target_folder="$CURRENT/nas-$nas_folder"
	if [ -d "$target_folder" ]; then
		sudo umount $target_folder
		if [ $? -eq 0 ];then
			echo "success to umount $target_folder"
		else
			echo "fail to umount $target_folder"
		fi
	fi
done

read -n1 -p "Press any key to exit..."
```