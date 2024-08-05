---
title: "Clash上网软件"
linkTitle: "Clash"
weight: 40
date: 2021-11-23
description: >
  Remmina 是一个上网软件。
---



### 下载安装

https://github.com/Dreamacro/clash/releases

下载 clash-linux-amd64-v1.4.2.gz 文件，解压缩之后移动:

```
chmod +x clash-linux-amd64
mv clash-linux-amd64 clash
sudo mv clash /usr/local/bin/
```

执行 `clash` 进行初始化：

```bash
$ clash
INFO[0000] Can't find config, create a initial config file 
INFO[0000] Can't find MMDB, start download              
INFO[0000] HTTP proxy listening at: 127.0.0.1:7890  
```

此时生成的配置文件在 `~/.config/clash/config.yaml` 中，可以配置clash的接口、参数、链接信息等。
ip数据库文件地址是 `~/.config/clash/config.yaml/Country.mmdb`。

### 配置 clash

修改 `~/.config/clash/config.yaml` 文件，默认生成的内容只有port一个参数:

```
port: 7890
```

退出clash，修改配置文件为：

```
#http代理
# port: 7890
#socks代理
# socks-port: 7891
# redir-port: 7892
# tproxy-port: 7893

mixed-port: 7890
allow-lan: true
bind-address: "*"
#运行模式: 规则Rule,全局Global,直连Direct
mode: rule
#log-level: silent
log-level: info
#管理ip和端口
external-controller: '0.0.0.0:9090'
#管理密码
secret: '12345678'
```

然后配置的其他内容，如各种服务器，需要从代理提供商那边获取，通常会给一个url，比如 `https://efanyun.me/clash/11629/3xNXXXXX/` ，用浏览器访问这个地址将文件下载下来，将里面的服务器配置信息复制到上面的配置文件中。

```
dns:
  enable: true
  # listen: 0.0.0.0:53
  ipv6: false

  default-nameserver:
    - 223.5.5.5
    - 119.29.29.29
    - 114.114.114.114
  enhanced-mode: redir-host
  fake-ip-range: 198.18.0.1/16
  use-hosts: true
  nameserver:
    - https://dns.alidns.com/dns-query
    - https://dns.rubyfish.cn/dns-query
    - https://223.5.5.5/dns-query
    - https://dns.pub/dns-query
  fallback:
    - tls://8.8.8.8:853
    - tls://dns.rubyfish.cn:853
    - https://1.0.0.1/dns-query
    - https://public.dns.iij.jp/dns-query
    - https://dns.twnic.tw/dns-query
  fallback-filter:
    geoip: true
    ipcidr:
      - 240.0.0.0/4
      - 0.0.0.0/32

proxies:
- name: 香港1
......
```

然后启动clash，从日志能看到：

```
$ clash
INFO[0000] Start initial compatible provider 故障转移       
INFO[0000] Start initial compatible provider 自动选择       
INFO[0000] Start initial compatible provider 节点选择       
INFO[0000] Mixed(http+socks5) proxy listening at: :7890 
INFO[0000] RESTful API listening at: 0.0.0.0:9090 
```

浏览器打开控制台地址：

http://clash.razord.top/

在控制台页面，点击 "设置" -> "外部控制设置"，填入地址：

- Host：127.0.0.1
- 端口： 9090
- 密钥： 12345678

之后就可以通过控制台页面进行配置了，但要注意的是：控制台页面操作的结果并不会保存到配置文件，只能是临时生效。



### 参考文档

- [Linux使用clash](https://cndaqiang.github.io/2020/07/17/clash/)
- [使用 Clash 科学上网](https://xxty847.github.io/2020/02/19/%E4%BD%BF%E7%94%A8Clash%E7%A7%91%E5%AD%A6%E4%B8%8A%E7%BD%91/)