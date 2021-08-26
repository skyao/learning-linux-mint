---
title: "修改Linux Mint的快捷键"
linkTitle: "快捷键修改"
weight: 222
date: 2021-08-26
description: >
  修改Linux Mint默认的快捷键，避免冲突
---

默认安装之后的 linux mint 的部分按键会和一些关键应用发生冲突，因此考虑修改。

## 避免和IntelliJ Idea冲突

1. ctrl + alt + left/right

    在 idea 中，ctrl + alt + left/right 用于在光标在文件的上一个未知/下一个位置之间跳转，非常方便。

    但是默认 linux mint 是将这个快捷键分配给了工作区的上一个工作区/下一个工作区，直接冲突了。

    修改方式，"系统设置" --> "键盘" --> "快捷键" --> "工作区"。

    > 注: 我一般喜欢设置为 `ctrl + shift + left/right`

2. ctrl + alt + L

	在idea中这个快捷键用来格式化代码，默认 linux mint 是将这个快捷键分配给了锁定屏幕。

	修改方式，"系统设置" --> "键盘" --> "快捷键" --> "系统" --> "锁定屏幕"。

    > 注: 我一般喜欢设置为 `ctrl + alt + delete`，默认 linux mint 中这个快捷键是给注销用的，考虑到注销极少使用，所以分配给锁屏，顺便和windows下的使用习惯保持一致。

## 工作区快捷键

默认工作区的几个快捷键都是 `ctrl + alt + (left|right|up|down)` ，上面为了避免和 IntelliJ Idea 冲突，我们修改了 ctrl + alt + left/right，为了保持一致，其他几个快捷键也相应修改过来。这样连续使用时，左手按住 ctrl + shift, 右手按 上下左右就可以关联到4个不同的快捷键，比较方便。

修改方式，"系统设置" --> "键盘" --> "快捷键" --> "常规":

- "显示窗口选择屏幕" 修改为 `Shift+Ctrl+Down`
- "显示工作区选择屏幕" 修改为 `Shift+Ctrl+Up`

## 多窗口快捷键

为了方便多个窗口之间切换，

- "在打开的窗口间循环" 默认是 "Alt + Tab"，这个和windows/mac是一致的，保持不变。
- "在同一应用打开的窗口间循环" ，默认没有快捷键，设置为 "Alt + Up"
- "在同一应用打开的窗口间逆向循环" ，默认没有快捷键，设置为 "Alt + Down"