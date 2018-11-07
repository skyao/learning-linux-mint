---
date: 2018-11-07T09:05:00+08:00
title: autojump
menu:
  main:
    parent: "daily-tool"
weight: 325
description : "autojump"
---

### 安装

```bash
sudo apt-get install autojump
```

安装完成之后如果直接运行autojump，会报错如下：

```bash
$ autojump
Please source the correct autojump file in your shell's
startup file. For more information, please reinstall autojump
and read the post installation instructions.
```

在`~/.bashrc`文件中加入如下内容，然后关闭再重新打开命令行：

```bash
source /usr/share/autojump/autojump.bash
```

### 参考资料

- [Linux 使用 autojump 直达目录](https://huangzz.xyz/linux-uses-autojump-direct-directory.html)
- https://github.com/wting/autojump/issues/346