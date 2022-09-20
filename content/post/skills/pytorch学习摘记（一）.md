---
title: "Pytorch学习摘记（一）"
description: "pytorch学习摘记（一）"
keywords: "pytorch学习摘记（一）"

date: 2020-12-02T15:52:17+08:00
lastmod: 2020-12-02T15:52:17+08:00

categories:
  - 技术积累
tags:
  - pytorch
  - 深度学习
# categories:技术积累、论文阅读、问题解决、算法刷题、其他等四个条目，其余放在tags里面。

# 原文作者
# Post's origin author name
#author:
# 原文链接
# Post's origin link URL
#link:
# 图片链接，用在open graph和twitter卡片上
# Image source link that will use in open graph and twitter card
#imgs:
# 在首页展开内容
# Expand content on the home page
#expand: true
# 外部链接地址，访问时直接跳转
# It's means that will redirecting to external links
#extlink:
# 在当前页面开启或关闭评论功能
# Switch to enabled or disabled comment plugins in this post
#comment:
#  enable: false
# 开启文章目录功能
# Enable table of content
#toc: false
# 绝对访问路径
# Absolute link for visit
#url: "pytorch学习摘记（一）.html"
# 开启文章置顶，数字越小越靠前
# Sticky post set-top in home page and the smaller nubmer will more forward.
#weight: 1
---

pytorch 学习的入门，一些基本的概念名词

<!--more-->


这几天除了看吴恩达的视频，也找了几本书看一下。   
# 深度学习网络架构   
- 前馈型神经网络   
- 卷积神经网络（CNN）  
- 循环神经网络（RNN）   
## pytorch 三特性   
- 与python完美结合   
- 张量计算   
- 动态计算图   
#### 张量【tensor】   
- 【张量即为pytorch的计算单元】   
- 一阶张量及一维数组，通常叫做向量[vector]   
- 二阶张量即二维数组，通常叫做矩阵[matrix]   
#### 尺寸【size】   
- 即一个张量每个维度的大小称为张量在这个维度上的尺寸 
#### pytorch里的计算图   
- 接触tensorflow等机器学习框架的朋友们对计算图的概念应该不陌生。pytorch与这些框架不一样的地方，pytorch可以通过**自动微分变量**自动实现计算图的构建。只要采用了自动微分变量，就可以利用.backward()自动进行反向传播。可以通过`x.gard`方法查看梯度信息
- 自动微分变量有三个属性`data`、`grad`、`grad_fn`。   
- 注：自动微分变量，在0.4及之后的版本中，就等同于张量。且pytorch规定，只有计算图的叶子节点才可以通过`.backward()`获得梯度信息。   
## 数据的分批处理   

- 设置batch_size,也就是把所有的训练集划分成一个批次大小的数据集，在每个训练周期内给神经网络输入一批数据，从而减少训练所需要的时间。   
 ## 后记   
- 都说CV方向的人都喜欢造词语，显得高大上，诚然，晦涩的词语会显得高大上，但是实际上没啥作用，只要理解了其实质，用A还是用B都无所谓了。（当然，有了标准化的表述，还是用术语名词吧）   
