---
title: "输入法"
linkTitle: "输入法"
weight: 10
date: 2024-01-20
description: >
  输入法
---

## 安装fcitx

如果安装操作系统时选择的是安装英文版本，则需要先安装 fcitx

```bash
sudo apt install fcitx
```

打开 “开始菜单” -> “Preferences” -> “Input method”，可以看到输入法已经默认为fcitx：

点击 “Simplified Chinese” ，找到 "Intall the language support package"，点击之后的 “install” 开始安装语言包。

## 启用输入法

重启，之后 打开 "fcitx configuration"，在 "Input method configuration" 的 "Input Method" 中通过点 "+" 增加 "Sunpinyin"

## 设置输入法

### 设置菜单

右键菜单中选择"配置"，然后在"外观"中设置 "字体大小" 为 32, "字体" 和 "菜单字体" 为 "文泉驿等宽微米黑 Regular"，不然输入法的选字菜单会太小看的很累。

在 "全局配置" 中设置候选词个数为 10 （最大可设置值）。

"全局配置" 中上一页修改为 `,`，下一页修改为 `.` ，方便前后翻页选词。

### 设置皮肤

右键菜单中选择"皮肤"，设置为 "经典"。

备注："默认"皮肤菜单背景色为白色文字，"暗色"皮肤则菜单背景颜色为黑色，"经典"则是在默认白色背景+红色/青色文字的基础上编号的颜色会更深一些。

