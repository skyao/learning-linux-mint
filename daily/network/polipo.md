# polipo

tags: polipo

shadowsock 是 socks5 的代理，有些程序对 socks5 的支持不好，此时需要提供额外的 http 代理。

因此我们引入 polipo，在 shadowsock 提供的 socks5 代理的基础上提供 http 代理。

## 安装

```bash
sudo apt-get install polipo
```

然后打开配置文件 `/etc/polipo/config`, 设置 ParentProxy 为 Shadowsocks:

```bash
socksParentProxy = "localhost:11080"
socksProxyType = socks5
```

保存配置修改之后重启 polipo:

```bash
sudo service polipo restart
```

## 使用

之后执行命令时加入 `http_proxy=http://localhost:8123` 如 `http_proxy=http://localhost:8123 curl ip.gs` 即可。

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


