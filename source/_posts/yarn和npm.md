---
title: yarn和npm
date: 2020-05-05 13:17:57
tags:
---

### 1.优缺点对比

yarn的优点？
1. 速度快：1、并行安装，执行包安装任务队列的时候，npm是按照队列执行的，必须要等到当前的package安装完毕后，再进行后面的package安装，而yarn是同步执行的；
2. 离线模式，如果之前已经安装过一个软件包，用Yarn再次安装时之间从缓存中获取，就不用像npm那样再从网络下载了，npm有提到但没有实现；
3. 安装版本统一，为了防止拉取到不同的版本，Yarn 有一个锁定文件 (lock file) 记录了被确切安装上的模块的版本号。每次只要新增了一个模块，Yarn 就会创建（或更新）yarn.lock 这个文件。这么做就保证了，每一次拉取同一个项目依赖时，使用的都是一样的模块版本。npm也有一个package-lock.json的文件，里面记录了依赖的版本号，但npm只是大版本号相同，比如：8.0.33，但在实际安装的时候可能安装的是高于8.0.33版本的，比如：8.0.35，如果开发者没有遵守大版本差异的话就可能出现不兼容的情况；
4. 输出日志更加简洁，在使用npm安装package的时候，terminal的日志输出很乱，命令行里会不断地打印出所有被安装上的依赖，而yarn只显示了必要的信息；
5. 网络适应：单个请求失败不会导致安装失败，请求失败时会重试。(在安装的过程中切换到vpn就很实用了)；
6. yarn依赖结构是扁平化的，npm2之前是树形的，npm3以上是扁平化的（这对于基于Unix的操作系统来说只不过是一个小烦恼，但对于Windows来说却是个破坏性的东西，因为有很多程序无法处理超过260个字符的文件路径名），防止出现多个副本导致空间浪费；

```
树形结构：
node_modules
- package-A
-- node_modules
--- package-B
----- node_modules
------ package-C
-------- some-really-really-really-long-file-name-in-package-c.js
```

### 2.命令对比
| npm | yarn |
| --- | --- |
|  npm install | yarn |
|  npm install react --save | yarn add react |
|  npm uninstall react --save | yarn remove react |
| npm install react --save-dev | yarn add react --dev |
| npm update --save | yarn upgrade |
| npm install webpack webpack-cli webpack-dev-server | yarn add webpack webpack-cli webpack-dev-server |

初始化的时候：npm install/yarn
--save 安装到项目的dependencies下
--save-dev 安装到项目的devDependencies下

### 3.其它
cnpm（[链接](https://developer.aliyun.com/mirror/NPM)）：只是npm使用了淘宝镜像后的别名



