---
title: aosp编译
date: 2020-04-14 21:32:54
tags:
---

### AOSP镜像：清华大学源
https://mirror.tuna.tsinghua.edu.cn/help/AOSP/

注意：repo sync后文件才会显示出来

### 编译
https://www.jianshu.com/p/895f0f26f769
```
cd aosp
source build/envsetup.sh
# 选一个你想编译的版本
lunch 
# 编译-j线程数量：cpu核心数量*2
make -j4

emulator

# 或者指定内存大小来运行模拟器
# 运行虚拟机，指定内存为2G
emulator -partition-size 2048
 
```



### 报错
```
 There is insufficient memory for the Java Runtime Environment to continue.
# Native memory allocation (mmap) failed to map 88080384 bytes for committing reserved memory.
# Possible reasons:
#   The system is out of physical RAM or swap space
#   The process is running with CompressedOops enabled, and the Java Heap may be blocking the growth of the native heap
# Possible solutions:
#   Reduce memory load on the system
#   Increase physical memory or swap space
#   Check if swap backing store is full
#   Decrease Java heap size (-Xmx/-Xms)
#   Decrease number of Java threads
#   Decrease Java thread stack sizes (-Xss)
#   Set larger code cache with -XX:ReservedCodeCacheSize=
#   JVM is running with Unscaled Compressed Oops mode in which the Java heap is
#     placed in the first 4GB address space. The Java Heap base address is the
#     maximum limit for the native heap growth. Please use -XX:HeapBaseMinAddress
#     to set the Java Heap base and to place the Java Heap above 4GB virtual address.
```

出现这种错误的时候，可以根据里面的solutions，最简单的解决方案是make后面接上-j参数


### aosp相关

环境相关的配置
build/core/envsetup.mk

OUT_DIR是通过参数传进去的，其它文件的输出在OUT_DIR下面，比如soong，target，host等

如果没有指定的话，OUT_DIR是当前aosp的目录下的out文件夹

手动指定，它的本质上是读你当前的环境变量的配置，如果你配置了则使用你的，没有配置的话就上面所说的路径
export OUT_DIR=your_out_dir
注意：export OUT_DIR=
OUT_DIR 后面直接跟= ，不要有空格。否则报错。

soong构建相关的资料
https://source.android.com/setup/build


### LineageOS
https://blog.csdn.net/zhonglunshun/article/details/89852565
