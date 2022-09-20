---
title: "吴恩达深度学习课程（计算图和pytorch动态计算梯度）"
description: "吴恩达深度学习课程（计算图和pytorch动态计算梯度）"
keywords: "吴恩达深度学习课程（计算图和pytorch动态计算梯度）"

date: 2020-12-04T16:14:44+08:00
lastmod: 2020-12-04T16:14:44+08:00

categories:
  - 算法刷题
tags:
  - 深度学习入门
  - 逻辑回归
  - pytorch

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
#url: "吴恩达深度学习课程（计算图和pytorch动态计算梯度）.html"
# 开启文章置顶，数字越小越靠前
# Sticky post set-top in home page and the smaller nubmer will more forward.
#weight: 1
---

吴恩达深度学习课程（计算图和pytorch动态计算梯度）
计算图以及pytoch动态计算图代码构建
<!--more-->

## 计算图   
- 初次接触计算图，还以为计算图是什么高深的东西，其就是表述了一个计算过程，是用来描述运算的有向无环图【图中自左向右计算，自有向左是一个反向传播过程】   
![](http://upccaishu.top:5120/images/big/797bbd3e5eee5c4a66a0ab990f279c22.PNG)   
- 上图表示的计算过程就是 `J=3*(a+b*c)`   
##  pytorch中的计算图自动构建   
- pytorch中的计算图dynamic computation graph(DCG)——即动态计算图   
- 下图为对上图中的计算图的pytorch代码实现   

```python   
import torch   
from torch.autograd import Variable   AAAdef DCG():   
    a = Variable(torch.Tensor([5]), requires_grad=True) # requires_grad 表示是否对其求梯度，默认是False   
    b = Variable(torch.Tensor([3]), requires_grad=True)   
    c = Variable(torch.Tensor([2]), requires_grad=True)   
    u = b*c   
    v = a+u   
    J = 3*v   
    J.backward()  # 进行反向传播，自动构建计算图   
    print(a.grad)   
    print(b.grad)   
    print(c.grad)   
    print(u.grad_fn)   
    print(v.grad_fn)   
    print(J.grad_fn)   

```   

    - 输出结果   
    tensor([3.])   
    tensor([6.])   
    tensor([9.])   
    <MulBackward0 object at 0x0000012FF265C208>   
    <AddBackward0 object at 0x0000012FF265C208>   
    <MulBackward0 object at 0x0000012FF265C208>   
#### pytorch中的一些参数说明   
- backward：当调用backward函数时，只有requires_grad为true以及is_leaf为true的节点才会被计算梯度，即grad属性才会被赋予值。   
- data: 变量中存储的值，如x中存储着1，y中存储着2，z中存储着3   
- requires_grad：该变量有两个值，True 或者 False，如果为True，则加入到反向传播图中参与计算。   
    
- **grad：该属性存储着相关的梯度值。当requires_grad为False时，该属性为None。即使requires_grad为True，也必须在调用其他节点的backward()之后，该变量的grad才会保存相关的梯度值。否则为None**   
- grad_fn：表示用于计算梯度的函数。返回值例子：`<AddBackward0 object at 0x0000012FF265C208>`   
- is_leaf：为True或者Falsejiedain，表示该节点是否为叶子节点。【只有是叶子结点才会存有梯度信息，否则grad为None】   
- retain_grad ：执行该方法，可以保存计算过程中非叶子节点的梯度信息。   AAA   
## 后记   
- 今天看到一句话，感觉还不错：观人与酒后，观人于忽略，观人于临财临富。   
- 现在突然想继续保持对网络安全的热枕，无论是社会工程还是纯技术。   