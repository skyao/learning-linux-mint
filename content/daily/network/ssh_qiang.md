---
date: 2018-11-07T13:05:00+08:00
title: SSH代理服务器
menu:
  main:
    parent: "daily-network"
weight: 344
description : "SSH代理服务器"
---

SSH 可以实现最为快捷的代理服务器，在没有其他代理服务器软件的情况下，可以作为一个临时解决方案使用。

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