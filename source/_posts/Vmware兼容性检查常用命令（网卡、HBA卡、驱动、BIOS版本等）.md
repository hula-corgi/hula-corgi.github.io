---
title: Vmware兼容性检查常用命令（网卡、HBA卡、驱动、BIOS版本等）
date: 2019-09-01 22:04:43
tags: vmware
---
### 检查前准备
1. 登录[VMware兼容性检查网站](https://www.vmware.com/resources/compatibility/search.php)
2. 进入ESXi的命令行界面
### 检查HBA卡和RAID卡
1. hba卡和raid卡的型号查看
``` bash
$ esxcfg-scsidevs -a
```
2. 检查hba卡的驱动版本
``` bash
$ vmkchdev -l | grep hba 
``` 
返回结果示例：8086:8d62 8086:7270 vmkernel vmhab0  
3. 在兼容性网站查看，选择I/O device，依次输入VID:DID SVID:SSID，有结果则表示符合兼容性要求
### 检查网卡
1. 检查网卡驱动
``` bash
$ vmkchdev -l | grep nic
``` 
2. 检查网卡型号
``` bash
$ esxcli network nic list 
``` 
### 查看bios版本
``` bash
$ smbiosDump | more 
``` 
### 查看各设备驱动版本
``` bash
esxcli software vib list | grep XXX 
``` 
### 参考
更详细方法请看该作者文章,[VMware 兼容性检查指北](https://www.v2ex.com/t/449039)