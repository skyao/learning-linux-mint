---
title: "Typora"
linkTitle: "Typora"
weight: 10
date: 2021-08-26
description: >
  非常漂亮的一个markdown编辑器，多平台通用
---

非常漂亮的一个markdown编辑器，和haroopad的左右两栏不同，typora是直接在一个界面中进行编辑和渲染。

我选择 typera 的理由： 1. 好用 2. 同时支持windows/linux/macos 三大平台

## 安装方式

https://typora.io/

安装方式，可以直接下载 deb 安装文件：

https://download.typora.io/linux/typora_1.9.3_amd64.deb

或者用 apt-get 安装：

```bash
wget -qO - https://typora.io/linux/public-key.asc | sudo tee /etc/apt/trusted.gpg.d/typora.asc
# add Typora's repository
sudo add-apt-repository 'deb https://typora.io/linux ./'
sudo apt-get update
# install typora
sudo apt-get install typora
```

### 跳过某个版本

使用时发现，原本正常的typora在升级到新版本之后就不能正常使用了，工具栏无法使用。反复卸载安装并清理本地缓存无效，最后只好跳过这个最新版本。

先看有哪些版本可选：

```bash
apt-cache madison typora
    typora |   0.11.6-1 | https://typora.io/linux ./ Packages
    typora |   0.11.2-1 | https://typora.io/linux ./ Packages
    typora |  0.10.11-1 | https://typora.io/linux ./ Packages
    typora |   0.9.98-1 | https://typora.io/linux ./ Packages
```

出问题的是最新的 0.11.6-1 版本，因此选择安装 0.11.2-1：

```bash
sudo apt install typora=0.11.2-1
```

然后就恢复正常了。

> 后续更新：第二天这个有问题的版本就被下线了。

参考:

- [Ubuntu通过apt-get安装指定版本和查询指定软件有多少个版本](https://www.cnblogs.com/EasonJim/p/7144017.html)

## 配置字体

Linux 下 typora 的字体不是太好看，而且字体是通过主题来设置的，并不能通过系统或者 typora来设置。

这意味着如果要修改字体，则需要去修改主题文件。

不过，typora 给了一个 "添加自定义css" 的方案，可以简单的搞定这个问题。

打开主题所在的目录，如 `/home/sky/.config/Typora/themes` ，新建一个 `base.user.css` 文件，

```bash
vi /home/sky/.config/Typora/themes/base.user.css
```

如果安装语言是中文，则内容为：

```css
body {
    font-family: "文泉驿等宽微米黑";
}

html,
body,
button,
input,
select,
textarea {
    font-family: "文泉驿等宽微米黑";
}

h1,
h2,
h3,
h4,
h5,
h6 {
    font-family: "文泉驿等宽微米黑";
}

pre,
code,
kbd,
tt,
var {
    font-family: "文泉驿等宽微米黑";
}
```

如果linux mint安装时选择的是英文版本而不是中文版本，则需要设置为:

```css
body {
    font-family: "WenQuanYi Micro Hei Mono Regular";
}

html,
body,
button,
input,
select,
textarea {
    font-family: "WenQuanYi Micro Hei Mono Regular";
}

h1,
h2,
h3,
h4,
h5,
h6 {
    font-family: "WenQuanYi Micro Hei Mono Regular";
}

pre,
code,
kbd,
tt,
var {
    font-family: "WenQuanYi Micro Hei Mono Regular";
}
```

这样就能修改所有主题的默认字体。

参考：

- [Add Custom CSS](https://support.typora.io/Add-Custom-CSS/)

