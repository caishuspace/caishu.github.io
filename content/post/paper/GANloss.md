---
title: "GANloss"
description: "GANloss"
keywords: "GANloss"

date: 2022-10-02T11:39:52+08:00
lastmod: 2022-10-02T11:39:52+08:00

categories:
  - 论文阅读
tags:
  - GAN 
  - GAN损失函数
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
#url: "ganloss.html"
# 开启文章置顶，数字越小越靠前
# Sticky post set-top in home page and the smaller nubmer will more forward.
#weight: 1
---

GANloss
- 原文链接：http://www.twistedwg.com/2018/10/05/GAN_loss_summary.html
<!--more-->

# GAN存在的问题
- GAN固有的问题有两个，其中一个是训练时容易梯度消失，另一个就是模型生成上多样性不足。针对这两个问题，改进的文章也是相继诞生，可谓百花争放。 WGAN的前作和后作将GAN本身的问题进行了详细的分析。
文章指出GAN之所以会出现梯度消失是因为GAN的损失函数中的JS散度项在判别器优化很好的时候为log2时将会导致生成器的梯度消失，而JS散度在生成和真实分布流行上不重叠时， 是衡为log2的。文章也证实了生成和真实的分布很难有交叠，这样就会导致梯度消失的发生。另一个多样性不足的问题是由于GAN展开的KL项在生成和真实分布之间的惩罚不同， 导致生成器更倾向于生成已经骗过判别器的样本。详细的可参看我之间的博客分析：GAN存在的问题。
正是由于导致GAN的两个问题的罪魁祸首是它的损失函数的设计，所以一批论文就此诞生。

# GAN的Loss改进
- WGAN利用Earth Move代替JS散度去拉近生成和真实分布；WGAN-GP 是针对WGAN在满足Lipschitz限制条件时直接采用了weight clipping，这会导权重都集中在Clipping的附近，为了自适应满足Lipschitz限制， WGAN-GP提出了梯度惩罚;WGAN-LP也是将WGAN上加上梯度惩罚，我们放在一起说； 同样的DRAGAN同样对在GAN的基础上加上梯度惩罚，不过是在原始GAN的基础上； LSGAN中利用最小二乘的思想去设计损失函数，展开后可以通过参数控制凑出皮尔森卡方散度也是代替了原始GAN中的JS散度； 最后来说的就是利用Hinge Loss改进GAN的原始Loss，Hinge Loss首度使用在GAN下是Geometric GAN， Hinge Loss在支持向量机下应用很广，在GAN训练上依旧展示了很好的效果，目前最新的 SAGAN、BigGAN都采用这个损失函数。

![xKL0RH.png](https://s1.ax1x.com/2022/10/02/xKL0RH.png)

【自我纠正一点，GAN Loss是一种损失函数的形式，具体的判别器损失，和生成器损失，具体可以使用MSE，MAE，交叉熵损失等来具体实现】