---
date: 2018-11-07T09:05:00+08:00
title: 调整字体
menu:
  main:
    parent: "daily-tool"
weight: 323
description : "调整字体"
---

搜狗输入法安装之后，系统字体会发生变化，默认会变成楷体，非常不好看。

解决方案，删除下面的这两个字体文件

```bash
cd /usr/share/fonts/truetype/arphic
sudo rm -f ukai.ttc  uming.ttc
```

然后重启即可。
