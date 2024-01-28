---
title: "输入法"
linkTitle: "输入法"
weight: 421
date: 2024-01-20
description: >
  输入法
---

Linux mint 21.1（对应 ubuntu 22.04) 下不要安装搜狗输入法，安装完成之后无法使用，原因不明，看搜狗输入法的官方介绍也只支持到20.04,没有22.04的支持。所以放弃，用自带的 sunpinyin 就好了。

### 安装fcitx

由于是安装操作系统时选择的是安装英文版本，因此需要先安装 fcitx

```bash
sudo apt install fcitx
```

打开 “开始菜单” -> “Preferences” -> “Input method”，可以看到输入法已经默认为fcitx：

点击 “Simplified Chinese” ，找到 "Intall the language support package"，点击之后的 “install” 开始安装语言包。

### 启用输入法

重启，之后 打开 "fcitx configuration"，在 "Input method configuration" 的 "Input Method" 中通过点 "+" 增加 "Sunpinyin"