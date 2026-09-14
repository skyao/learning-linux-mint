---
title: "FileZilla"
linkTitle: "FileZilla"
weight: 80
date: 2021-08-26
description: >
  使用 FileZilla 进行 ftp/sftp 文件传输
---

windows 下我现在统一使用 filezilla 进行 ftp/sftp 文件传输, linux 这边也尽量保持一致吧.

## 安装

### 下载

下载页面:

https://filezilla-project.org/download.php?platform=linux64

直接下载地址:

https://dl2.cdn.filezilla-project.org/client/FileZilla_3.69.3_x86_64-linux-gnu.tar.xz?h=-MZF88L9qY_9njOrYhbEhg&x=1762748574

### 解压缩

解压缩下载下来的 FileZilla_3.69.3_x86_64-linux-gnu.tar.xz 文件, 放到 `/home/sky/work/soft` 目录.

```bash
tar xvf FileZilla_3.69.3_x86_64-linux-gnu.tar.xz -C /home/sky/work/soft
```

### 启动器

在 `/home/sky/work/soft/FileZilla3/bin` 目录下打开 filezilla 即可，但比较麻烦，还是建一个启动器比较方便。

执行如下命令：

```bash
cat > ~/.local/share/applications/filezilla.desktop <<'EOF'
[Desktop Entry]
Type=Application
Version=1.0
Name=FileZilla
GenericName=FTP Client
Comment=Cross-platform FTP, FTPS and SFTP client
Exec=/home/sky/work/soft/FileZilla3/bin/filezilla
Icon=/home/sky/work/soft/FileZilla3/share/icons/hicolor/480x480/apps/filezilla.png
Terminal=false
Categories=Network;FileTransfer;GTK;
Keywords=FTP;SFTP;FTPS;SSH;FileZilla;
StartupNotify=true
MimeType=x-scheme-handler/ftp;
EOF

# 刷新菜单 + 注册 ftp:// 链接
update-desktop-database ~/.local/share/applications
xdg-mime default filezilla.desktop x-scheme-handler/ftp
```

验证一下语法没问题(没有输出就是没问题):

```bash
desktop-file-validate ~/.local/share/applications/filezilla.desktop
```

打开开始菜单搜 "FileZilla",图标就出来了,右键可"固定到面板/任务栏"，也可以用 Synapse 唤起 filezilla.

## 使用

使用方式和界面和 windows 下基本一致.

### site manager 文件备份

```bash
ls -la ~/.config/filezilla/ 2>/dev/null || ls -la ~/.filezilla/ 2>/dev/null
```

输出为:

```bash
drwx------  2 sky sky  4096 Sep 14 10:21 .
drwxr-xr-x 36 sky sky  4096 Sep 14 10:16 ..
-rw-rw-r--  1 sky sky  8483 Sep 14 10:21 filezilla.xml
-rw-rw-r--  1 sky sky   364 Sep 14 10:13 hostkeys.xml
-rw-rw-r--  1 sky sky   286 Sep 14 10:21 layout.xml
-rw-r--r--  1 sky sky     0 Sep  7 21:01 lockfile
-rw-r--r--  1 sky sky 28672 Sep  7 21:01 queue.sqlite3
-rw-rw-r--  1 sky sky   959 Sep 14 10:13 sitemanager.xml
```

只要备份并同步这个 sitemanager.xml 文件就可以了。

也可以通过图形界面操作，打开 site manager 之后，右键 my sites 选 export 即可。导入时从 File --> import






