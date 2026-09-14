---
title: "终端设置"
linkTitle: "终端"
weight: 50
date: 2021-08-26
description: >
  修改Linux Mint的默认的终端设置
---

## 终端操作

注意 Shift 是通用"夺回控制权"键，很多操作如果发现操作不了时，比如右键发现弹不出右键菜单，就可以按住 shift 再右键。

### 复制/粘贴内容

在终端中选择内容， 可以按住 shift 键再拖动。

复制/粘贴命令： 	Ctrl+Shift+C / Ctrl+Shift+V 或者鼠标中键

Shift+拖选 → Ctrl+Shift+C → Ctrl+Shift+V，推荐这个操作方式。

### 打开右键菜单

正常右键就能呼出右键菜单，但是在某些时候，比如 vi 打开文件时，右键打不开菜单。这时按住 shift 即可。

### 显示菜单栏

默认不显示菜单栏， 可以右键呼出菜单后，选择 "Show menubar"。

也可以直接修改默认行为，改为默认就显示菜单栏：

```bash
gsettings set org.gnome.Terminal.Legacy.Settings default-show-menubar true
```

