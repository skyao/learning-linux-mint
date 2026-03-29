---
title: "重置多屏设置"
linkTitle: "重置多屏设置"
weight: 340
date: 2021-08-26
description: >
  接多个屏幕时，如果遇到历史设置混乱不好调整，可以重置
---

我用的是 Cinnamon 桌面，只要简单转移走 Cinnamon 的专属显示配置文件，就可以清除历史设置：

```bash
mv ~/.config/cinnamon-monitors.xml ~/.config/cinnamon-monitors.xml.bak
```

之后再外界显示器，就可以重新开始正常设置。

设置好之后，再次执行mv命令进行备份。

