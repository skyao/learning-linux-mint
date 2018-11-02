# 设置DNS

设置阿里的DNS，提高网络响应速度, 实测效果明显。

## 做法

打开终端执行:

```bash
sudo vim /etc/resolvconf/resolv.conf.d/tail
```

添加下面两行Alidns：

```bash
nameserver 223.5.5.5
nameserver 223.6.6.6
```

保存后执行:

```bash
sudo resolvconf -u
```

查看 `/etc/resolv.conf` 可以看到多了上面两条 nameserver.