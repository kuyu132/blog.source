---
title: nginx配置详解
date: 2020-04-10 08:25:47
tags:
---

### nginx -v/V
-v nginx的版本
-V conf脚本执行时候的arguments

### nginx使用

启动和停止服务
sudo service nginx restart
sudo service nginx start
sudo service nginx stop
//快速重新加载配置，无需停止nginx服务
sudo nginx -s reload

测试配置是否OK
nginx -t

<!--more-->

默认配置和nginx.conf之间的区别
/etc/nginx/sites-available/default
/etc/nginx/nginx.conf

在nginx的配置文件中可以查看log日志文件位置
/var/log/nginx/access.log
/var/log/nginx/error.log

### 默认html位置
/usr/share/nginx/html

### 配置文件位置
/etc/nginx/nginx.conf

### 并发
工作进程数量
worker_processes

单个进程并发量
worker_connections

总并发 = worker_processes * worker_connections

### server服务器虚拟主机，可以配置多个


比如：
```
server {
  #默认端口
  listen *:80;
  #域名解析
  server_name git.kuyu.com;
  server_tokens off;
  root /opt/gitlab/embedded/service/gitlab-rails/public;

  client_max_body_size 250m;

  access_log  /var/log/gitlab/nginx/gitlab_access.log;
  error_log   /var/log/gitlab/nginx/gitlab_error.log;
  
  #配置默认访问页
  location / {
    root html;
    index index.html index.htm;
  }
  
  #配置错误页面
  location = /50x.html{
  root html;
  }sudo 
}

```


### http包含的指令块
http server upstream location 

## 常见错误
1. nginx: [error] invalid PID number "" in "/run/nginx.pid"
nginx没有启动

2. nginx: [emerg] getpwnam("nginx") failed in /etc/nginx/nginx.conf:1
nginx中没有nginx这个用户


### nginx配置php
由于pi-dashboard是用php实现了，所以要搭php的nginx环境

find -name "*fpm.sock"
php-fpm.sock

./run/php/php7.3-fpm.sock


#### php fpm位置
/etc/php/7.3/fpm

显示php主进程
ps -ef|grep php-fpm

fpm配置文件路径
/etc/php/7.3/fpm/php-fpm.conf
/etc/php/7.3/fpm/pool.d/www.conf

fpm启动服务(根据安装的版本号)
sudo service php7.3-fpm start 

