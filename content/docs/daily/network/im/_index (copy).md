---
title: "discord"
linkTitle: "discord"
weight: 10
date: 2021-08-26
description: >
  Linux Mint下discord的安装使用
---



### 下载

https://discord.com/download

### 安装

deb标准安装



### 正确的启动方式

命令行启动：

```bash
$ discord --proxy-server=http://192.168.0.30:7890
```

也可以增加一个桌面启动方式，然后进入目录 `/usr/share/discord`， `sudo vi discord.desktop`修改 ：

```properties
Exec=/usr/share/discord/Discord --proxy-server=http://192.168.0.30:7890
```

在这里增加代理配置。之后点这个图标就能带着代理信息启动discord了。

参考:

- https://www.nonozero.com/archives/198.html
- https://xcel.me/howto-set-proxy-for-discord-app-on-linux/



### 附录：代理问题

启动之后卡在 update 界面，估计是网络被墙了。在命令行中启动discord，可以看到日志：

```bash
$ discord       
Discord 0.0.17
Starting app.
Starting updater.
[Modules] Modules initializing
[Modules] Distribution: remote
[Modules] Host updates: enabled
[Modules] Module updates: enabled
[Modules] Module install path: /home/sky/.config/discord/0.0.17/modules
[Modules] Module installed file path: /home/sky/.config/discord/0.0.17/modules/installed.json
[Modules] Module download path: /home/sky/.config/discord/0.0.17/modules/pending
[Modules] No updates to install
[Modules] Checking for host updates.
Error downloading with electron net: network timeout: https://discord.com/api/updates/stable?platform=linux&version=0.0.17
Falling back to node net library..
[Modules] Host is up to date.
[Modules] Checking for module updates at https://discord.com/api/modules/stable/versions.json
Error downloading with electron net: network timeout: https://discord.com/api/modules/stable/versions.json
Falling back to node net library..
......
```

开启全局翻墙之后，可以顺利通过上面报错的地方，但是又会报错 

```bash
[WebContents] did-fail-load -200 ERR_CERT_COMMON_NAME_INVALID retry in 1000 ms
(node:60932) electron: Failed to load URL: https://discordapp.com/app?_=1651047018860 with error: ERR_CERT_COMMON_NAME_INVALID
(Use `discord --trace-warnings ...` to show where the warning was created)
[WebContents] retrying load https://discordapp.com/app?_=1651047018860
[WebContents] did-fail-load -200 ERR_CERT_COMMON_NAME_INVALID retry in 2526.0695510375936 ms
(node:60932) electron: Failed to load URL: https://discordapp.com/app?_=1651047018860 with error: ERR_CERT_COMMON_NAME_INVALID
[WebContents] retrying load https://discordapp.com/app?_=1651047018860
[WebContents] did-fail-load -200 ERR_CERT_COMMON_NAME_INVALID retry in 4139.532933476243 ms
(node:60932) electron: Failed to load URL: https://discordapp.com/app?_=1651047018860 with error: ERR_CERT_COMMON_NAME_INVALID
```

但这个问题似乎不会影响 discord 的启动。全局翻墙之后 discord 可以正常使用。

尝试过，设置 all_proxy, http_proxy 等方式对 discord 无效。