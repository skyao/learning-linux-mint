---
title: "[归档]SSH代理服务器"
linkTitle: "[归档]SSH代理服务器"
weight: 999
date: 2021-08-26
description: >
  SSH 可以实现最为快捷的代理服务器，在没有其他代理服务器软件的情况下，可以作为一个临时解决方案使用。
---

{{% pageinfo color="primary" %}}
实测： 很不稳定，没有使用价值。可能是服务器端那边做了检查和防范。
{{% /pageinfo %}}

## 代理服务器

1. 建立隧道

    在本地执行以下命令:

    ```bash
    ssh -D 10085 remote_server_address
    ```

2. 设置代理

	在浏览器中设置代理服务器连接为 "socket4"，链接到 "127.0.0.1/10085" 端口。

## 翻墙

如果远程服务器在国外, 那么这个 ssh 代理服务器 就实现了 `翻墙` 的功能.

工作原理和用 putty 设置 dynamic 是一样的.

