---
title:  uefi 硬盘下windows 与linux 双系时改变引导首选项为linux
date: 2015-02-04 10:51:11
tags:
---
我最近把引导模式改成了 UEFI +GPT，但是发现，改成这个之后，又装了双系统，
windows 8.1 +fedora 但是我想把fedora 改为第一启动项，上网上搜了一下，
有个easyUEFI的工具可以管理，也有linux 但是使用之后发现，没有我想要的效果，
我还是自已来吧，
//使windows 启动项启效
1.    我用fedora 在ESP分区中修改ms文件夹中的文件名
//     在fedora的引导 中建立windows 引导
2.    因为我的fedora的启动引导中有windows的引导项，
但是那是以前的文件的位置，我们要手动的改一下，
//    改变linux 下的GRUB的引导下的windows 的引导的位置 
3 .     vi /boot/grub/grub.conf
我的是把ms 下的Boot 文件夹名改为了 Boot2 那么我们把引导的位置改为Boot2 就好了，
重启： windows 正常引导