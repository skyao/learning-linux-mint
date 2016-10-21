# 使用终端做ssh client

发现 putty 和 Remmina 做 ssh 客户端都不是太好用, 远不如 windows 平台上的 securyCrt 和 putty.

后来看到很多人都推荐直接用linux的终端做 ssh client, 简单敲个 "ssh server_name" 就连上去了，体验上也和和本地一致。

## 自动登录

为了减少每次敲击密码的麻烦, 还可以通过authorized_keys的方式来自动登录：

1. 上传本机的 `.ssh/id_isa.pub` 文件到服务器端

2. 在远程服务器上运行

    ```bash
    cat ~/id_rsa.pub >> ~/.ssh/authorized_keys
    ```

3. 在本机终端中输入 "ssh server_address" 即可自动登录