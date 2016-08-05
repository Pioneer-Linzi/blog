---
title: arch linux中的jdk的安装
date: 2016-06-12 10:51:11
tags: linux
---

编辑/etc/pacman.conf, 在文件末尾添加以下内容(操作前请做好相应备份)
```
[archlinuxcn]
SigLevel = Optional TrustedOnly
Server = http://mirrors.163.com/archlinux-cn/$arch
```
之后安装 archlinuxcn-keyring 包导入 GPG key 从甲骨文的官网
```
	pacman -S jdk
```


this all 
thanks