---
title: "安装搜狗输入法"
linkTitle: "搜狗输入法"
weight: 422
date: 2022-01-20
description: >
  搜狗输入法
---

### 安装fcitx

由于是安装操作系统时选择的是安装英文版本，因此需要先安装 fcitx


```bash
sudo apt install fcitx
```

打开 “开始菜单” -> “Preferences” -> “Input method”，可以看到输入法已经默认为fcitx：

点击 “Simplified Chinese” 之后的 “install” 开始安装。

## 安装搜狗拼音输入法

安装步骤如下：

1. 进入搜狗输入法官网，下载 Linux 64位版本

    https://pinyin.sogou.com/linux/

    最新版本已经明确申明稳定支持 ubuntu 20.04

    在终端中执行命令：

    ```bash
    sudo dpkg -i sogoupinyin_3.4.0.9700_amd64.deb
    ```

3. 重启系统，完成安装


## 设置输入法

重启之后，再次打开输入法/Input method，会看到只有一个英文输入法。

点 "+" 号增加新的输入法，搜索 "sogou"，注意去掉 "only show current langurage"的勾选，就会找到 sogoupinyin

"Global Config" 里面可以看到相关的设置：

![](images/fcitx-3.jpg)

部分细节：

1. 切换输入法的快捷键是 `Ctrl+Space`
2. 上一页的快捷键是 `-` 或者 `,`
3. 下一页的快捷键是 `=` 或者 `.`
4. "Candidate Word Number"用来设置候选词的个数


## 修复

偶尔会遇到搜狗输入法异常，此时解决的方式是删除`.config/SogouPY`目录，然后重新启动电脑。

注意：尝试过重新启动搜狗输入法，无效，还是需要重启机器。


## 调整字体

搜狗输入法安装之后，系统字体会发生变化，默认会变成楷体，非常不好看。

解决方案，删除下面的这两个字体文件

```bash
cd /usr/share/fonts/truetype/arphic
sudo rm -f ukai.ttc  uming.ttc
```

然后重启即可。

