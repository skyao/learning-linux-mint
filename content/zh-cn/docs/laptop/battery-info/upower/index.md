---
title: "upower"
linkTitle: "upower"
weight: 10
date: 2021-08-26
description: >
  Cinnamon 自带，可查看电池健康与容量
---


```bash
➜  ~ upower -i /org/freedesktop/UPower/devices/battery_BAT0
  native-path:          BAT0
  vendor:               CeIxpe
  model:                5B10W51815
  serial:               45
  power supply:         yes
  updated:              Mon 28 Sep 2026 07:07:19 AM CST (12 seconds ago)
  has history:          yes
  has statistics:       yes
  battery
    present:             yes
    rechargeable:        yes
    state:               fully-charged
    warning-level:       none
    energy:              58.32 Wh
    energy-empty:        0 Wh
    energy-full:         60.04 Wh
    energy-full-design:  57 Wh
    energy-rate:         0 W
    voltage:             17.183 V
    charge-cycles:       1
    percentage:          97%
    capacity:            100%
    technology:          lithium-polymer
    icon-name:          'battery-full-charged-symbolic'
```