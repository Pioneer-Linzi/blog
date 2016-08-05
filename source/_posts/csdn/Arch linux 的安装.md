---
title: Arch linux 的安装
date: 2016-06-12 10:51:11
tags: linux
---
## arch linux 的安装
家里有一台300块买的台式机，感觉就装这个比较好一点，本文是自用与学习的记录，有不少配置是没有配置的，这是自己总结的感觉比较好设置一点的
##参考
	http://bbs.archlinuxcn.org/viewtopic.php?id=1037
## U盘的制作
我用的是linux 下的 dd 
```
dd  if=xxx.iso of=/dev/sdb bs=1M
```
## 开机启动到U盘
我用的UEFI ,这里我们开机用UEFI启动模式，启动到Arch linux 
```
	# ls /sys/firmware/efi/efivars 
```
## 这里的键盘布局 连接到因特网，更新系统时间都省略
## 识别设备
```
	# lsblk
```
## 分区工具
这里我用的是cfdisk 
```
	#cfdisk /dev/sda
```
## 分区
看自已分吧，这里不细说了
## 格式化分区
```
	mkfs.ext4 格式化为Ext4格式 
    为让 genfstab 能生成fstab时包含 交换分区，须先激活交换分区
    mkswap 格式化为swap用swapon命令激活 
```
## 修改源 
这里我用的是163的源
x86_64用下面这个
```
Server = http://mirrors.163.com/archlinux/$repo/os/$arch
```

i686用这个
```
	Server = http://mirrors.163.com/archlinux/$repo/os/i686
	Server = http://mirrors.sohu.com/archlinux/$repo/os/i686
```

## 安装基础系统
```
	# pacstrap -i /mnt base base-devel
```
## 安装syslinux 
```
	pacman -S syslinux
```
## 更新syslinux
```
	syslinux-install_update -iam
```
## 修改syslinux配置文件
```
	修改正确的/boot/syslinux/syslinux.cfg
    中的Root分区，把wr 改为ro
```
**这里要注意root 目录的设备的设定** 

## 启用开机网络
```
	systemctl enable dhcpcd
```
## 添加管理员密码
```
	passwd 
```
## 添加用户
```
	
    useradd -m -g users  -s /bin/bash linzi
    添加用户密码
```
## 安装xorg
```
	pacman -Syy
    pacman -S xorg
```
## 安装xfce4 
```
	pacman -S xfce4
```
## 安装chromium
```
	pacman -S chromium
```
## 中文乱码问题
pacman -S wqy-zenhei ttf-fireflysung(flash乱码)
## bash: ifconfig: command not found
```
sudo pacman -S net-tools dnsutils inetutils iproute2

```