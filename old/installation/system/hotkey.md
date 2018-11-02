# 快捷键修改

默认安装之后的 linux mint 的部分按键会和一些关键应用发生冲突，因此考虑修改。

## IntelliJ Idea

1. ctrl + alt + left/right

    在 idea 中，ctrl + alt + left/right 用于在光标在文件的上一个未知/下一个位置之间跳转，非常方便。

    但是默认 linux mint 是将这个快捷键分配给了工作区的上一个工作区/下一个工作区，直接冲突了。

    修改方式，"系统设置" --> "键盘" --> "快捷键" --> "工作区"。

    > 注: 我一般喜欢设置为 `ctrl + shift + left/right`

1. ctrl + alt + L

	在idea中这个快捷键用来格式化代码，默认 linux mint 是将这个快捷键分配给了锁定屏幕。

	修改方式，"系统设置" --> "键盘" --> "快捷键" --> "系统" --> "锁定屏幕"。

    > 注: 我一般喜欢设置为 `ctrl + alt + delete`，默认 linux mint 中这个快捷键是给注销用的，考虑到注销极少使用，所以分配给锁屏，顺便和windows下的使用习惯保持一致。

## 工作区

默认工作区的几个快捷键都是 `ctrl + alt + (left|right|up|down)` ，上面为了避免和 IntelliJ Idea 冲突，我们修改了 ctrl + alt + left/right，为了保持一致，其他几个快捷键也相应修改过来。这样连续使用时，左手按住 ctrl + shift, 右手按 上下左右就可以关联到4个不同的快捷键，比较方便。

修改方式，"系统设置" --> "键盘" --> "快捷键" --> "常规":

- "切换 缩放" 修改为 `Shift+Ctrl+Down`
- "切换 展览" 修改为 `Shift+Ctrl+U`