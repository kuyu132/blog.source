---
layout: ph-1
title: AndroidRoot教程
date: 2020-05-06 15:02:46
tags:
  - root
  - essential phone
---
### 常用命令 

##### 重启到bootloader
adb reboot bootloader

##### 刷入recovery到a分区
./fastboot flash boot_a recovery.img

##### 刷入root boot到a分区
./fastboot flash boot_a P-090-root-boot.img

##### 查看当前激活分区
./fastboot getvar current-slot

<!--more-->

##### 激活某个分区
./fastboot --set-active=b

##### 普通解锁后支持刷写第三方 recovery、boot、官方系统镜像以及拥有官方签名的 bootloader；而完全解锁则进一步支持刷写第三方 bootloader。
./fastboot flashing unlock_critical

./fastboot flashing unlock

### 其它
刷机技巧：http://www.ucu520.top/?p=467

官网地址：https://www.essential.com/developer/current-builds

常用刷机命令：https://ghost.atibm.com/adb-an-zhuo-shua-ji-chang-yong-de-adbhe-fastbootming-ling/

### 刷机文件详解
<img src="/images/ph-1.png" width="640px"/>

##### abl.img
好像是高通平台的文件

##### bluetooth.img
蓝牙

##### boot.img
boot.img是Android系统启动所必须加载的文件。简单的说，boot.img包含两部分，分别为kernel 和ramdisk。
当你的Android手机启动时首先会启动RADIO，然后是SPL。
此时SPL 会根据你的按键，确定进入哪个模式（ 例如Recovery，Fastboot等等），
如果没有按其他键，那么spl 会将kernel 载入到记忆体中，ramdisk 也会载入到你的设备的根目录。

##### cmnlib.mbn
百度百科：mbn是高通包含了特定运营商定制的一套efs，nv的集成包文件。同样的mbn文件会有很多。每个运营商都会有一个特定mbn包含在modem的代码中。需要使用高通最新的PDC工具load和激活（PDC工具之前为QPST software download的子功能，现在作为一个单独的app包含在QPST中）。然后才能切换。
mbn文件是刷高通ril芯片的文件，需要用高通的QPST软件烧录。
mbn直接是个文件，不需要解压，把QPST切换到software download—Multi-image，这个sheet就可以识别mbn文件烧录。

##### flashall.sh/flashall.bat
刷机的脚本

##### modem.img
基带相关，射频相关的参数

##### nvdef.img

##### system.img
系统镜像

##### vendor.img
vendor分区相关，带有品牌标识和驱动

##### xbl.img
xbl分区相关

[bootloader资料](https://www.bilibili.com/read/cv307758/)

[essential-phone的资料](https://zhuanlan.zhihu.com/p/58507641)

