---
title: pytorch
date: 2020-05-05 22:38:41
tags:
---
安装cpu的pytorch，使用官网的安装方式，import的时候一直报"no module named torch"

推荐使用下面的方式安装并创建deeplearning环境(名称可以自己定义)
```
conda create -n deeplearning pytorch torchvision -c pytorch
conda activate deeplearning
conda deactivate
```
