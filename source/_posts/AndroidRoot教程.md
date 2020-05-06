---
layout: ph-1
title: AndroidRoot教程
date: 2020-05-06 15:02:46
tags:
  - root
  - essential phone
---
### 

fastboot flash boot twrp-3.2.3-0-mata.img && fastboot reboot

adb reboot bootloader

./fastboot --set-active=b

./fastboot flash boot_a recovery.img

//查看当前激活分区
./fastboot getvar current-slot


./fastboot flashing unlock_critical

./fastboot flashing unlock


刷机技巧：http://www.ucu520.top/?p=467

https://zhuanlan.zhihu.com/p/58507641

官网地址：https://www.essential.com/developer/current-builds

常用刷机命令：https://ghost.atibm.com/adb-an-zhuo-shua-ji-chang-yong-de-adbhe-fastbootming-ling/
