---
title: "关闭屏幕"
linkTitle: "关闭屏幕"
weight: 330
date: 2021-08-26
description: >
  关闭屏幕的方式
---



最近经常从 macbook 运行 vs code 来 remote ssh 到 linux mint 主机上进行开发，遇到一个小问题：就是 linux mint 的主机屏幕如果不关闭，我就无法在 Macbook 上直接使用显示器（我的3台4k显示器分别有两组线材连接到台式机和macbook），我必须一个一个显示器去调整输入信号为macbook，非常麻烦。

解决的方法有两种。

## 闲置超时自动关闭屏幕

在 linux mint 的系统设置（system settings）中中，Power Options 选项中设置 "Turn off the screen when inactive for" ，但很遗憾最小的时间为 5分钟。

这个方式可用，单等5分钟是不能忍的。这还不如直接关机再重启呢，20秒之内可以重新启动完成。

在下面还有一个 "when the power button is pressed"，在windows下可以选择关闭屏幕，但是 linux mint 里面没有关闭屏幕的选项，最多只能选 "Lock Screen"。

只能找其他的方法。

## 通过命令来关闭屏幕

google了一圈，发现这个命令可以用在 linux mint上：

```bash
cinnamon-screensaver-command -l; xset dpms force off;
```

如果遇到报错:

```bash
xset:  unable to open display ""
```

则需要设置 `DISPLAY` 环境变量为 `:0.0`，为了避免造成其他影响就不直接修改 .zshrc 文件了，改在命令中增加 export 内容：

```bash
cinnamon-screensaver-command -l; export DISPLAY=:0.0;xset dpms force off;
```

实测可用。

### 添加alias命令

为了方便使用，在 .zshrc 中增加 alias:

```bash
alias turn-off-screens='cinnamon-screensaver-command -l;export DISPLAY=:0.0;xset dpms force off;'
```

需要关闭屏幕时只需要执行 `turn-off-screens` 就好了。

### 添加快捷键

增加一个命令，在 `/usr/local/bin` 创建` shortcut_turn_off_screen.sh`文件，

```bash
sudo vi /usr/local/bin/shortcut_turn_off_screen.sh
```

内容为：

```bash
bash -c "cinnamon-screensaver-command -l;export DISPLAY=:0.0;xset dpms force off;"
```

记得设置可执行权限：

```bash
sudo chmod +x /usr/local/bin/shortcut_turn_off_screen.sh
```

然后在 linux mint 的 System Settings 中选择 Keyboard -> Shortcuts -> Custom Shortcuts，"add custom shortcut"。名称设置为"turn off screen"，命令为:

```/usr/local/bin/shortcut_turn_off_screen.sh
/usr/local/bin/shortcut_turn_off_screen.sh
```

再分配一个快捷键，为了方便和醒目我就直接把锁屏键（也就是 super + L）用来关闭屏幕了。

直接就可以一键关闭屏幕！赞

## 参考资料

- [power management - xset: unable to open display - Ask Ubuntu](https://askubuntu.com/questions/476036/xset-unable-to-open-display)
- [解决xset: unable to open display ""问题_草原苍狼的博客-CSDN博客_xset: unable to open display](https://blog.csdn.net/jeffreyst_zb/article/details/8585544)
- [Script to lock and turn off the screen on linux mint · GitHub](https://gist.github.com/hugomaiavieira/c4208dec84d0c7115712)
- [Turn off Display - Linux Mint Forums](https://forums.linuxmint.com/viewtopic.php?t=284898)
