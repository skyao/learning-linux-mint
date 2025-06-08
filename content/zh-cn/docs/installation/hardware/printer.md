---
title: "安装Epson L4160打印机"
linkTitle: "安装打印机"
weight: 215
date: 2021-12-93
description: >
  Ubuntu下安装配置Epson L4160打印机
---

## 打印机驱动

### 本地usb连接

本地安装，用usb线连接Epson L4160打印机。

先下载linux驱动：

1. https://epson.com/Support/wa00821
2. drivers ，输入产品型号 L4160
3. 下载 ESC / P-R Driver (generic driver) / Epson Printer Utility / All-in-one package，注意选择x64版本的deb

4. 安装下载好的deb

再在系统中选择打印机，然后添加打印机，此时会自动识别出 EPSON-L4160-Series，添加即可。

### wifi连接

断开usb，删除本地打印机。

在打印机上设置好wifi之后，再打开设置中的打印机，发现已经自动识别了，貌似不需要设置。



