---
title: "Timeshift 系统备份"
linkTitle: "Timeshift"
weight: 270
date: 2021-08-27
description: >
  使用 Timeshift 进行系统备份和恢复
---

## 备份

使用 timeshift 的图形界面，可以很方便的进行系统备份。

## 恢复

同样使用 timeshift 的图形界面，可以很方便的进行系统恢复。

和 debian 12 相比，有图形界面操作方便一些。

## 紧急恢复

重点是紧急情况下的恢复，主要是系统出现问题时，已经无法进入系统启动 timeshift，甚至连 恢复模式都无法进入。

这时候需要使用 livecd 启动系统，然后使用 timeshift 进行恢复。

### 使用 livecd 启动系统

下载 livecd 镜像，如我使用的是最新的 linux mint 22.1 iso，使用 rufus 制作启动盘，或者其他制作启动盘的工具，然后从 u盘启动进行 linux mint 的 livecd 系统。

### 准备 timeshift

在 livecd 系统中，默认已经安装有 timeshift 了，可以直接使用。

```bash
$ sudo apt install timeshift
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
timeshift is already the newest version (24.06.6+xia).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

验证：

```bash
$ timeshift

Timeshift v24.06.6 by Tony George (teejeetech@gmail.com)
......
```

查看硬盘分区，找出来存放 timeshift 备份资料的硬盘分区：

```bash
$ lsblk -f

NAME        FSTYPE   FSVER LABEL   UUID                                 FSAVAIL FSUSE% MOUNTPOINTS
loop0       squashfs 4.0                                                      0   100% /rofs
sda                                                                                    
├─sda1                                                                                 
└─sda2      ntfs           data2   F48682FD8682BF9A                       16.2T     1% /media/mint/data2
sdb                                                                                    
├─sdb1      exfat    1.0   Ventoy  4E21-0000                                           
└─sdb2                                                                                 
nvme0n1                                                                                
├─nvme0n1p1 vfat     FAT32         CE01-9336                                           
├─nvme0n1p2                                                                            
├─nvme0n1p3 ntfs           win11   DA5E38635E383A99                                    
├─nvme0n1p4 ntfs                   6AB8BA8AB8BA5473                                    
├─nvme0n1p5 ntfs           windata 6E7A55257A54EB7B                                    
├─nvme0n1p6 ext4     1.0           7f899256-56e1-4b0f-aa86-a98009417b08  665.8G     6% /media/mint/7f899256-56e1-4b0f-aa86-a98009417b08
├─nvme0n1p7 ext4     1.0           f9cde109-c5a3-4be4-861c-bfd11a4f8c01  149.3G    15% /media/mint/f9cde109-c5a3-4be4-861c-bfd11a4f8c01
└─nvme0n1p8 exfat    1.0   data    6E51-13F3                               1.8T     1% /media/mint/data
```

这里的 nvme0n1p7 是我存放 timeshift 备份资料的硬盘分区。记录下它的 UUID f9cde109-c5a3-4be4-861c-bfd11a4f8c01。另外注意 nvme0n1p1 这个 fat32 分区是 efi 分区，后面会用到。

修改 timeshift 配置文件，设置备份硬盘分区：

```bash
$ sudo nano /etc/timeshift.json
```

找到 `"backup_device": null,` 这一行，修改为：

```json
"backup_device": "UUID=f9cde109-c5a3-4be4-861c-bfd11a4f8c01",
```

检查当前 timeshift 备份情况：

```bash
$ sudo timeshift --list

First run mode (config file not found)
Selected default snapshot type: RSYNC
Mounted '/dev/nvme0n1p7' at '/run/timeshift/3932/backup'
Live Session detected, backup is disabled.
Device : /dev/nvme0n1p7
UUID   : f9cde109-c5a3-4be4-861c-bfd11a4f8c01
Path   : /run/timeshift/3932/backup
Mode   : RSYNC
Status : OK
4 snapshots, 160.3 GB free

Num     Name                 Tags  Description                       
------------------------------------------------------------------------------
0    >  2024-12-07_09-47-24  O D   apt upgrade and install software  
1    >  2024-12-07_10-59-16  O     install whitesur and plank        
2    >  2025-02-01_20-09-22  O D   apt upgrade                       
3    >  2025-06-07_22-00-01  D                   
```

还好在系统崩溃前一天，有一个 daily 的自动备份，可以用来恢复系统。

### 恢复系统

```bash
sudo timeshift --restore
```

第一步是选择恢复到哪个备份，我选择的是 2025-06-07_22-00-01 这个备份。

```bash
First run mode (config file not found)
Selected default snapshot type: RSYNC
Mounted '/dev/nvme0n1p7' at '/run/timeshift/3969/backup'
Live Session detected, backup is disabled.

Select snapshot:

Num     Name                 Tags  Description                       
------------------------------------------------------------------------------
0    >  2024-12-07_09-47-24  O D   apt upgrade and install software  
1    >  2024-12-07_10-59-16  O     install whitesur and plank        
2    >  2025-02-01_20-09-22  O D   apt upgrade                       
3    >  2025-06-07_22-00-01  D                                       

Enter snapshot number (a=Abort, p=Previous, n=Next): 3
```

第二步是选择恢复到哪个硬盘分区，也就是操作系统 root 所在的硬盘分区。我这里选择的是 `/dev/nvme0n1p6` 这个分区：

```bash
******************************************************************************
To restore with default options, press the ENTER key for all prompts!
******************************************************************************

Press ENTER to continue...

Select '/' device (default = /dev/nvme0n1p6):

Num     Device              Size  Type  Label  
------------------------------------------------------------------------------
0    >  /dev/nvme0n1p6  819.2 GB  ext4         
1    >  /dev/nvme0n1p7  204.8 GB  ext4         

[ENTER = Default (/dev/nvme0n1p6), r = Root device, a = Abort]

Enter device name or number: 0
```

第三步是选择 `/boot/efi` 所在的硬盘分区，我选择的是 `/dev/nvme0n1p1` 这个分区：

```bash
******************************************************************************
'/' will be on 'nvme0n1p6'
******************************************************************************

Select '/boot/efi' device (default = /dev/nvme0n1p1):

Num     Device              Size  Type  Label  
------------------------------------------------------------------------------
0    >  /dev/nvme0n1p6  819.2 GB  ext4         
1    >  /dev/nvme0n1p7  204.8 GB  ext4         

[ENTER = Default (/dev/nvme0n1p1), r = Root device, a = Abort]
```

第四步是选择是否重新安装 GRUB2 引导程序，我选择的是重新安装，安装路径为默认的 `/dev/nvme0n1`：

```bash
******************************************************************************
'/boot/efi' will be on 'nvme0n1p1'
******************************************************************************

Re-install GRUB2 bootloader? (recommended) (y/n): y

Select GRUB device:

Num     Device     Description                        
------------------------------------------------------------------------------
0    >  sda        ATA TOSHIBA MG09ACA18TE [MBR]      
1    >  sdb        SSSTC CV SSSTC CVB-8D128-HP [MBR]  
2    >  nvme0n1     YSSDHB-4TN7000 [MBR]              
3    >  nvme0n1p6   ext4, 819.2 GB GB                 
4    >  nvme0n1p7   ext4, 204.8 GB GB                 

[ENTER = Default (/dev/nvme0n1), a = Abort]

Enter device name or number (a=Abort): 
```

之后备份开始，会提示数据将会在哪些设备上修改：

```bash
******************************************************************************
GRUB Device: /dev/nvme0n1
******************************************************************************

======================================================================
WARNING
======================================================================
Data will be modified on following devices:

Device          Mount    
--------------  ---------
/dev/nvme0n1p6  /        
/dev/nvme0n1p1  /boot/efi
```

恢复的日志如下：

```bash
......
......
# 忽略文件复制内容
......
......
......
sent 136,537,349 bytes  received 26,063 bytes  13,006,039.24 bytes/sec
total size is 20,035,908,269  speedup is 146.72

Updated /etc/fstab on target device: /run/timeshift/4101/restore/etc/fstab
Parsing log file...
Archiving: /run/timeshift/4101/backup/timeshift/snapshots/2025-06-07_22-00-01/rsync-log-restore

Re-installing GRUB2 bootloader...
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported.

Updating GRUB menu...
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/50_linuxmint.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.8.0-52-generic
Found initrd image: /boot/initrd.img-6.8.0-52-generic
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
grub-probe: error: cannot find a GRUB drive for /dev/sdb2.  Check your device.map.
Found Windows Boot Manager on /dev/nvme0n1p1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings ...
done

Syncing file systems...

Cleaning up...
run-parts: executing /etc/timeshift/restore-hooks.d/50_linuxmint

Restore completed
------------------------------------------------------------------------------
Checking file systems for errors...
fsck from util-linux 2.39.3
e2fsck 1.47.0 (5-Feb-2023)
/dev/nvme0n1p6 is mounted.
e2fsck: Cannot continue, aborting.


fsck from util-linux 2.39.3
fsck.fat 4.2 (2021-01-31)
There are differences between boot sector and its backup.
This is mostly harmless. Differences: (offset:original/backup)
  65:01/00
  Not automatically fixing this.
Dirty bit is set. Fs was not properly unmounted and some data may be corrupt.
 Automatically removing dirty bit.

*** Filesystem was changed ***
Writing changes.
/dev/nvme0n1p1: 204 files, 37647/98304 clusters

E: Failed to remove directory
Ret=256
```

最后时刻有些报错，忽略即可。备份操作已经完成，文件已经复制到目标硬盘分区，引导程序也已经安装完成。

重启机器，正常进入系统。
