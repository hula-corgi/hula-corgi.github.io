---
title: Vmware Tools常用命令（安装、重启、恢复、卸载）
date: 2019-09-01 21:50:31
tags: vmware
---
## 安装
### Windows
1. 通过vCenter或者Console控制台点击安装VMware Tools，对应的ISO映像被挂载到客户机操作系统中。
2. 点击 setup64.exe开始安装，选择完全安装，不需要重启操作系统，完成后系统托盘会出现VM图标。
3. （可选）点击设备管理器-显示适配器-VMware SVGA-更新驱动（C:\Program Files\Common Files\VMware\Drivers\video_wddm），该步骤在Server 2012以后不再需要
### Linux
1. 通过vCenter或者Console控制台点击安装VMware Tools，对应的ISO映像被挂载到客户机操作系统中。
2. 进入安装路径
``` bash
$ cd /media/VMware\ Tools   
``` 
对于CenotOS 7.3,需要先挂载：
``` bash
$ mkdir /mnt/cdrom
$ mount -t auto /dev/cdrom /mnt/cdrom
$ cd /mnt/cdrom
```  
3. 拷贝到其他路径后解压，执行
``` bash
$ 运行 vmware-install.pl
```
4. 安装完成后，在虚拟机的Summary状态栏也可以看到VMware工具的状态。
5. 升级VMware：右键虚拟机-客户机操作系统-升级VMware Tools

## 重启
### Linux
对于centos 6/redhat 6:
``` bash
$ /etc/vmware-tools/services.sh restart
```
对于centos 7:
``` bash
cd /etc/vmware-tools/
```
service vmware-tools restart

## 重置
### Linux
``` bash
$ 运行 /usr/bin/vmware-config-tools.pl 
```

## 卸载
### Linux
``` bash
$ 运行 vmware-uninstall-tools.pl
```