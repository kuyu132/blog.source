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



