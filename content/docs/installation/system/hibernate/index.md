---
title: "关闭休眠"
linkTitle: "关闭休眠"
weight: 60
date: 2021-08-26
description: >
  关闭Linux Mint的休眠
---

## 关闭休眠

```bash
sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target
```

正常能看到输出为:

```bash
Created symlink /etc/systemd/system/sleep.target → /dev/null.
Created symlink /etc/systemd/system/suspend.target → /dev/null.
Created symlink /etc/systemd/system/hibernate.target → /dev/null.
Created symlink /etc/systemd/system/hybrid-sleep.target → /dev/null.
```

重启后查看:

```bash
sudo systemctl status sleep.target suspend.target hibernate.target hybrid-sleep.target
```

正常能看到四种状态都被禁用：

```bash
○ sleep.target
     Loaded: masked (Reason: Unit sleep.target is masked.)
     Active: inactive (dead)

○ suspend.target
     Loaded: masked (Reason: Unit suspend.target is masked.)
     Active: inactive (dead)

○ hibernate.target
     Loaded: masked (Reason: Unit hibernate.target is masked.)
     Active: inactive (dead)

○ hybrid-sleep.target
     Loaded: masked (Reason: Unit hybrid-sleep.target is masked.)
     Active: inactive (dead)
```

另外打开 power management，设置：

- "suspend when inactive for": never
- "when the power button is pressed: Lock Screen

## 参考资料

- [https://cn.linux-console.net/?p=1266](如何在 Linux 中禁用挂起和休眠模式)