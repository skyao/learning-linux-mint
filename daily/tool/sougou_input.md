# 搜狗输入法

## 安装

安装步骤如下：

1. 进入搜狗输入法官网，下载 Linux 64位版本

	http://pinyin.sogou.com/linux/?r=pinyin

	最新版本已经支持 Ubuntu12.04、14.04及16.04，而且对 linux mint 18 的支持非常好。

2. 在终端中执行命令：

	```bash
	sudo dpkg -i sogoupinyin_2.1.0.0086_amd64.deb
    ```

3. 重启系统，完成安装


## 设置

打开 "开始菜单" -> "首选项" -> "输入法"，可以看到输入法已经默认为fcitx：

![](images/fcitx.jpg)

点击 "简体中文" 之后的 "安装" 开始安装。

打开 "开始菜单" -> "首选项" -> "Fcitx 配置", 设置如下：

![](images/fcitx-2.jpg)

"Global Config" 里面可以看到相关的设置：

![](images/fcitx-3.jpg)

部分细节：

1. 切换输入法的快捷键是 `Ctrl+Space`
2. 上一页的快捷键是 `-` 或者 `,`
3. 下一页的快捷键是 `=` 或者 `.`
4. "Candidate Word Number"用来设置候选词的个数

可以删除部分不需要的输入法：

![](images/fcitx-4.jpg)

## 修复

偶尔会遇到搜狗输入法异常，此时解决的方式是删除`.config/SogouPY`目录，然后重新启动电脑。

注意：尝试过重新启动搜狗输入法，无效，还是需要重启机器。


