---
title: ph1_root
date: 2020-05-21 10:40:30
tags:
---
### Essential Phone Root教程

注意：此教程是仅针对essential phone的root教程，不同手机root方法不同，只可借鉴，不可照搬

### 机型介绍
具体的介绍见链接，篇幅有点长就不写在这里了
[详细评测](https://baijiahao.baidu.com/s?id=1616184493684777930&wfr=spider&for=pc)

为啥root机型选这款？
1. 开放性，这款是安卓之父退出的一款机型，开放性比国内厂商高很多；
2. room完整性，官网上有从Android7.1.1~10所有的 [room链接](https://www.essential.com/developer/current-builds) ，可以刷至任意版本，并且民间也有很多第三方的room；
3. recovery完备，TWRP有专门对此机型开发的recovery，可以做很多其它的操作：比如刷入busy box、xposed等框架；
4. 配置及预算，部门预算有限，这款机型价格便宜，但配置是晓龙835的处理器 4GB内存 128G存储，在采购后今后3年内配置也是够的；

#### Android版本选择

由于Android10.0以后无法直接获取IMEI，在拿Android10中root的手机交给其它项目做开发的时候便遇到了这个问题，无法做到我们的工具获取IMEI的方式和app一致，所以选择了Android10.0的前一个版本：Android9

### root详细教程
#### 方式1：
[参见知乎专栏](https://zhuanlan.zhihu.com/p/58507641)

#### 方式2：
知乎专栏的方式是刷入recovery，然后刷入MagiskFace框架实现的，这里不需要刷入recovery，前面的步骤和知乎专栏上大体相同

1. oem解锁 

2. 刷入room，下载完成fastboot版本的room后，使用里面的flashall文件进行刷机操作，刷完后进入系统，确保系统是ok的；

3. 重启至bootloader模式，查看当前激活的分区，刷入boot root的img文件到当前的激活分区，重启即可；

4. 步骤3后重启进入系统后，会多出一个Magisk Face的应用，点击后发现无法使用，这个时候需要我们安装Magisk Face的apk应用，安装完后，打开显示正常即表示root成功；

### 常用命令

##### 1.重启到bootloader
adb reboot bootloader

##### 2.普通解锁后支持刷写第三方 recovery、boot、官方系统镜像以及拥有官方签名的 bootloader；而完全解锁则进一步支持刷写第三方 bootloader。
./fastboot flashing unlock_critical

./fastboot flashing unlock

##### 3.查看当前激活分区
./fastboot getvar current-slot

##### 4.刷入recovery到a分区
./fastboot flash boot_a recovery.img

##### 5.刷入root boot到a分区
./fastboot flash boot_a P-090-root-boot.img

##### 6.激活某个分区
./fastboot --set-active=b


