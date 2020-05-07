---
title: pytorch
date: 2020-05-05 22:38:41
tags:
hidden: true
---
安装cpu的pytorch，使用官网的安装方式，import的时候一直报"no module named torch"

推荐使用下面的方式安装并创建deeplearning环境(名称可以自己定义)
```
conda create -n deeplearning pytorch torchvision -c pytorch
conda activate deeplearning
conda deactivate
```
如果安装的时候没有指定环境的话，可以通过conda info --envs命令查看默认创建的，比如：base

<a style="color:red;">
注意：要在conda activate的深度学习环境的终端里面启动jupyter book，不然在引入的时候可能会出现no module named torch
</a>

### jupter notebook
安装：官网：https://jupyter.org/install.html

启动：https://blog.csdn.net/cruise_h/article/details/60337437
