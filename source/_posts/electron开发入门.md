---
title: electron开发入门
date: 2020-03-16 10:24:42
tags:
---

### 准备工作
1.安装node.js，[地址](https://nodejs.org/zh-cn/)

    1. 安装完毕后执行:node -v 查看node版本 
    
    2. node会同时帮你安装npm包管理工具，你也可以使用yarn来管理包，执行npm -v查看npm的版本
    
    注：npm和yarn的区别：npm是目录树包管理方式，yarn是平级包管理方式)

2.安装electron

    npm install -g electron
    
     -g：全局，没有权限的话前面加sudo

### 创建项目
方式一：
```
1. mkdir demo
2. cd demo
3. npm init
4. npm install electron
```
##### 关键步骤：
1. npm init，执行这个命令后会在项目的根目录创建一个package.json，这个是项目的配置文件，包括项目的名称、版本、脚本、依赖、构建脚本；
2. npm install electron执行这个命令后会在自动在devDependencies中添加electron的依赖；

这种方式需要你自己手动创建index.html，main.js和render.js等脚本

方式二：
```
1. git clone https://github.com/electron/electron-quick-start
2. cd electron-quick-start
3. npm install && npm start
```
这种方式对初学者比较友好，你只需要3步就能完成项目的创建及启动

### 主进程及渲染进程
前言：electron的本质是一个chromium
#### 1.主进程：main.js
只有一个，
    
#### 2.渲染进程：render.js

    
