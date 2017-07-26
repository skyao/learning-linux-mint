# polipo

tags: polipo

linux 下的 shadowsocks 不提供全局代理的功能，因此不得不寻找其他办法。

因此我们引入 polipo，在 shadowsocks 提供的 socks5 代理的基础上提供 http 代理。

## PAC全局代理

参考资料:

- [Ubuntu 16安装shadowsocks-qt5并使用PAC全局代理](https://www.litcc.com/2016/12/29/Ubuntu16-shadowsocks-pac/)

具体做法如下：

1. 安装 pip

	```bash
	sudo apt-get install python-pip
	pip install --upgrade pip
	```

2. 安装GenPAC

	GenPAC 是基于gfwlist的代理自动配置（Proxy Auto-config）文件生成工具，支持自定义规则。

	```bash
	sudo pip install setuptools
	sudo pip install genpac
	pip install --upgrade genpac
	```

3. 下载 gfwlist

	```bash
	genpac -p "SOCKS5 127.0.0.1:11080" --gfwlist-proxy="SOCKS5 127.0.0.1:11080" --gfwlist-url=https://raw.githubusercontent.com/gfwlist/gfwlist/master/gfwlist.txt --output="/home/sky/work/soft/pac/autoproxy.pac"
    ```

4. 网络设置中，"网络代理" 设置为 "自动设置"

	url指向我们前面生成的 pac 文件，如 `file:///home/sky/work/soft/pac/autoproxy.pac`

## HTTP全局代理

上面的 pac 全局代理方式，在有些情况下会无效，比如最常用的终端。主要时因为终端很多工具目前只支持 http 和 https 等协议，对 socks5 协议支持不够好.

参考下面这个文章的做法：

- [为终端设置Shadowsocks代理](http://droidyue.com/blog/2016/04/04/set-shadowsocks-proxy-for-terminal/)

首先需要安装配置好 polipo， 提供 http 代理，具体做法见 [前面内容](polipo.md)

### 使用方法

polipo 安装好之后，在终端执行命令时加入 `http_proxy=http://localhost:8123` 如 `http_proxy=http://localhost:8123 curl ip.gs` 即可。

为了方便，可以有两种优化方式：

1. 加别名

	在 `/etc/profile` 中增加下列内容：

	```bash
    alias hp="http_proxy=http://localhost:8123"
    ```

	需要时在命令前加 `hp` 即可，如 `hp curl ip.gs`。

2. 直接export

	如果觉得每次都加hp前缀麻烦，可以在 `/etc/profile` 中增加下列内容：

	```bash
    export http_proxy=http://localhost:8123
    ```

这样 shadowsocks 的 socks5 代理 和 polipo 的 http 代理配置，就可以覆盖绝大部分情况了。

## 使用策略

### 直接开启全局代理

直接开启全局代理的做法是：

1. 设置系统网络代理为自动，这样大部分网络请求都走代理了
2. `/etc/profile` 中直接加入 `export http_proxy=http://localhost:8123`

此时开机之后：

1. shadowsocks 自动启动，提供 sockes5 代理
2. polipo自动启动，在 shadowsocks 的基础上提供 http 代理
3. 系统网络通过本地 pac 文件决定是否走 sockes5 代理
4. 控制台等命令如果识别 http_proxy 则走 http 代理

测试过 chrome 浏览器，在安装 SwitchyOmega 的情况下，可以继续通过 SwitchyOmega 控制 chrome 的代理，"直接连接" / "系统代理" / "auto switch" 都可以工作。



### 需要时再开启全局代理


## 需要单独设置代理的情况


### npm

为 npm 设置代理

```bash
npm config set proxy http://localhost:8123
npm config set https-proxy http://localhost:8123
```