---
title: "acpi"
linkTitle: "acpi"
weight: 20
date: 2021-08-26
description: >
  acpi 的只读小工具
---

## 安装

```bash
# 1. 常规安装
sudo apt update
sudo apt install acpi

# 2. 验证
acpi --version && acpi -V
```

验证结果：

```bash
➜  ~ acpi --version && acpi -V
acpi 1.7

Copyright (C) 2001 Grahame Bowland.
              2008-2012 Michael Meskes.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```



## 用法

### 常用命令

| 命令         | 作用                        | 典型输出                                                     |
| ------------ | --------------------------- | ------------------------------------------------------------ |
| `acpi`       | 电池一行摘要                | `Battery 0: Discharging, 59%, 03:25:11 remaining`            |
| `acpi -b`    | 只要电池                    | 同上                                                         |
| `acpi -a`    | 电源适配器                  | `Adapter 0: on-line` / `off-line`                            |
| `acpi -b -i` | 加设计/满电容量             | `Battery 0: design capacity 4000 mAh, last full capacity 3210 mAh = 80%` |
| `acpi -t`    | 温度                        | `Thermal 0: ok, 46.0 degrees C`                              |
| `acpi -c`    | 冷却/风扇档位               | `Cooling 0: Processor 0 of 10`                               |
| `acpi -f`    | 温度用华氏                  | —                                                            |
| `acpi -V`    | 上面全部（= `-b -a -t -c`） | 一屏总览                                                     |
| `acpi -V -i` | 全部 + 电池详情             | 最常用组合                                                   |

示例：

```bash
➜  ~ acpi                     
Battery 0: Full, 97%

➜  ~ acpi -b                  
Battery 0: Full, 97%

➜  ~ acpi -a
Adapter 0: on-line

➜  ~ acpi -b -i
Battery 0: Full, 97%
Battery 0: design capacity 3317 mAh, last full capacity 3493 mAh = 100%

➜  ~ acpi -t   
Thermal 0: ok, 46.0 degrees C

➜  ~ acpi -c
Cooling 0: Processor 0 of 10
Cooling 1: SEN2 no state information available
Cooling 2: Processor 0 of 10
Cooling 3: x86_pkg_temp no state information available
Cooling 4: Processor 0 of 10
Cooling 5: Processor 0 of 10
Cooling 6: intel_powerclamp 0 of 100
Cooling 7: PCIe_Port_Link_Speed_0000:00:06.0 0 of 3
Cooling 8: INT3400 Thermal no state information available
Cooling 9: Processor 0 of 10
Cooling 10: TCPU no state information available
Cooling 11: Processor 0 of 10
Cooling 12: iwlwifi_1 no state information available
Cooling 13: Processor 0 of 10
Cooling 14: Processor 0 of 10
Cooling 15: TCC Offset 0 of 63
Cooling 16: PCIe_Port_Link_Speed_0000:00:1c.0 1 of 2
Cooling 17: SEN1 no state information available

➜  ~ acpi -V
Battery 0: Full, 97%
Battery 0: design capacity 3316 mAh, last full capacity 3493 mAh = 100%
Adapter 0: on-line
Thermal 0: ok, 46.0 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 128.0 degrees C
Cooling 0: Processor 0 of 10
Cooling 1: SEN2 no state information available
Cooling 2: Processor 0 of 10
Cooling 3: x86_pkg_temp no state information available
Cooling 4: Processor 0 of 10
Cooling 5: Processor 0 of 10
Cooling 6: intel_powerclamp 0 of 100
Cooling 7: PCIe_Port_Link_Speed_0000:00:06.0 0 of 3
Cooling 8: INT3400 Thermal no state information available
Cooling 9: Processor 0 of 10
Cooling 10: TCPU no state information available
Cooling 11: Processor 0 of 10
Cooling 12: iwlwifi_1 no state information available
Cooling 13: Processor 0 of 10
Cooling 14: Processor 0 of 10
Cooling 15: TCC Offset 0 of 63
Cooling 16: PCIe_Port_Link_Speed_0000:00:1c.0 1 of 2
Cooling 17: SEN1 no state information available

➜  ~ acpi -V -i
Battery 0: Full, 97%
Battery 0: design capacity 3317 mAh, last full capacity 3494 mAh = 100%
Adapter 0: on-line
Thermal 0: ok, 46.0 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 128.0 degrees C
Cooling 0: Processor 0 of 10
Cooling 1: SEN2 no state information available
Cooling 2: Processor 0 of 10
Cooling 3: x86_pkg_temp no state information available
Cooling 4: Processor 0 of 10
Cooling 5: Processor 0 of 10
Cooling 6: intel_powerclamp 0 of 100
Cooling 7: PCIe_Port_Link_Speed_0000:00:06.0 0 of 3
Cooling 8: INT3400 Thermal no state information available
Cooling 9: Processor 0 of 10
Cooling 10: TCPU no state information available
Cooling 11: Processor 0 of 10
Cooling 12: iwlwifi_1 no state information available
Cooling 13: Processor 0 of 10
Cooling 14: Processor 0 of 10
Cooling 15: TCC Offset 0 of 63
Cooling 16: PCIe_Port_Link_Speed_0000:00:1c.0 1 of 2
Cooling 17: SEN1 no state information available

```

### 持续观察放电

持续观察放电速率变化（拔电后挂上，看谁在偷电）：

```bash
Every 5.0s: acpi -V -i skyt14s: Mon Sep 28 07:33:40 2026
Battery 0: Discharging, 96%, 06:09:52 remaining
Battery 0: design capacity 3368 mAh, last full capacity 3548 mAh = 100%
Adapter 0: off-line
Thermal 0: ok, 45.0 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 128.0 degrees C
Cooling 0: Processor 0 of 10
Cooling 1: SEN2 no state information available
Cooling 2: Processor 0 of 10
Cooling 3: x86_pkg_temp no state information available
Cooling 4: Processor 0 of 10
Cooling 5: Processor 0 of 10
Cooling 6: intel_powerclamp 0 of 100
Cooling 7: PCIe_Port_Link_Speed_0000:00:06.0 0 of 3
Cooling 8: INT3400 Thermal no state information available
Cooling 9: Processor 0 of 10
Cooling 10: TCPU no state information available
Cooling 11: Processor 0 of 10
Cooling 12: iwlwifi_1 no state information available
Cooling 13: Processor 0 of 10
Cooling 14: Processor 0 of 10
Cooling 15: TCC Offset 0 of 63
Cooling 16: PCIe_Port_Link_Speed_0000:00:1c.0 1 of 2
Cooling 17: SEN1 no state information available
```

输出解读：

| 行                 | 值                | 含义                                                         |
| ------------------ | ----------------- | ------------------------------------------------------------ |
| `Battery 0`        | Discharging, 96%  | 拔电状态，下面全是放电特性                                   |
| 剩余时间           | 06:09:52          | 96% × 3548 mAh ≈ 3406 mAh ÷ 6.165 h ≈ **552 mA ≈ 6.3 W**（按 11.5 V 估）→ 空载功耗正常 |
| design / last full | 3368 / 3548 mAh   | **满电容量比设计容量还大 → 上报有问题，健康度作废**          |
| `Thermal 0`        | ok, 45.0 °C       | 空载 45 °C，对 1145G7 这类薄机身属正常偏凉                   |
| trip point         | critical @ 128 °C | 固件定义的关机红线，**不是当前温度，不用管**                 |
| 8 个 `Processor`   | 全是 `0 of 10`    | **当前零节流**，CPU 在完全放开的频点上                       |
| `TCC Offset`       | `0 of 63`         | 出厂默认节流点（TjMax 100 °C），没下调                       |
| `intel_powerclamp` | `0 of 100`        | 强制空闲散热未启用                                           |