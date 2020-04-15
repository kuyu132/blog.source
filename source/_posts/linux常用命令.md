---
title: linux常用命令
date: 2020-04-12 11:38:03
tags:
---
### 更改文件所有者及组
 chown user_name file_name
 chgrp group_name file_name

### 查找进程
ps -ef | grep nginx

### 查找文件夹
find / name


### 切换root用户
sudo su

切回普通用户：su - test
 
### 查看磁盘空间大小
df -hl

### 查看文件夹大小


### 显示vim行数
vim /etc/vim/vimrc
最后面添加
set nu
