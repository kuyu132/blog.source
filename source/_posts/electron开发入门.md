title: electron开发入门
date: 2020-03-16 10:24:42
tags:
  - electron
  - 入门
---

### 一、准备工作
1.安装node.js，[地址](https://nodejs.org/zh-cn/)

    1. 安装完毕后执行:node -v 查看node版本 
    
    2. node会同时帮你安装npm包管理工具，你也可以使用yarn来管理包，执行npm -v查看npm的版本
    
    注：npm和yarn的区别：npm是目录树包管理方式，yarn是平级包管理方式)

2.安装electron

    npm install -g electron
    
     -g：全局，没有权限的话前面加sudo

### 二、创建项目

<!--more-->

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

### 三、主进程及渲染进程
前言：electron的本质是一个chromium
#### 1.主进程
    入口：main.js
只有一个，electron将nodejs结合起来，提供了操作访问和操作本地资源的API，这些API原本是在浏览器中不存在的，比如：磁盘、文件访问等，同时它管理着渲染进程窗口的创建和销毁；
    
#### 2.渲染进程
    入口：render.js
Electron本质是浏览器，它的界面是用html展示的，渲染进程是负责渲染html的，它可以有多个，比如：
```$xslt
//main.js
const {BrowserWindow} = require('electron');
const window1 = new BrowserWindow({width: 200, height: 200})
const window2 = new BrowserWindow({width: 200, height: 200})

window1.loadURL('https://baidu.com');
window2.loadURL(`file://${__dirname}/index.html`)
```
这两个窗口一个加载的是外部url，一个是本地的文件，两者是相互独立的进程，如果window1出现崩溃的话，window2是不受影响的；

#### 3.任务管理器的展示
<img src="/images/electron_background.png" width="640px"/>

Electron：主进程
3个新的 Helper 应用程序变体
1.Electron Helper(GPU)：用于 GPU 进程
2.Electron Helper(Renderer).app：用于渲染器
3.Electron Helper(Plugin).app：用于插件

### 四、main.js详解

### 五、常见模块及使用
#### 模块的安装
#### package-lock.json文件介绍
    
### 六、打包

