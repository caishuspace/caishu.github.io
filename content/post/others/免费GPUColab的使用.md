---
title: "免费GPUColab的使用"
description: "免费GPUColab的使用"
keywords: "免费GPUColab的使用"

date: 2021-03-30T18:05:36+08:00
lastmod: 2021-03-30T18:05:36+08:00

categories:
  - 其他
tags:
  - 免费GPU
  -
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
#url: "免费gpucolab的使用.html"
# 开启文章置顶，数字越小越靠前
# Sticky post set-top in home page and the smaller nubmer will more forward.
#weight: 1
---

免费GPUColab的使用

由于实验需要，所需需要GPU做服务运算。大致搜了一下，国内也有几家可以免费使用的GPU，比如百度的飞浆，Kaggle Kernel等等，但是各有不足。其中百度的GPU只能使用其自己的深度学习框架，不能使用pytorch等第三方深度学习框架。后来使用了谷歌的Colab感觉还不错。- 由于众所周知的原因，访问colab需要科学上网，所以，如果没有这个途径的，可以直接略过此文章，选用别的免费GPU。

<!--more-->

# Colab介绍 
- 详情介绍- `https://research.google.com/colaboratory/faq.html#usage-limits` 
- 简单说一下，就是，colab虚拟机最长12小时，分配的GPU不定，且官方不提供任何说明性质的保证。大致有K80，T4，P4等，用的越少，分配好GPU的概率越大，越优先使用。 
# 使用步骤 
#### 登录Google Driver
Google Colab 支持挂载 Google Drive，方便存储文件。所以推荐直接从 Google Drive 登录。打开Google Drive 官网，使用gmail邮箱直接登陆。个人建议，代码，运行文件全部放在谷歌云盘内部，不要把文件按放进虚拟机，因为，虚拟机释放了，就啥也没了。云盘15G免费空间，一般足够用了。 
#### 在Google Driver 添加colaboratory应用\
云盘默认是没有Colab的，需要手动添加，然后打开使用就可以了。使用jupyter的文件方式打开，并链接虚拟主机。至于怎么在jupyter里使用命令行，在命令里面加一个`!`就可以了。 
- 打开，新建的文件夹，在其中右击空白处 --> More --> Connect more apps 
- 搜索“Colaboratory”，点击图标安装。 
- 安装完成后，右击空白处 --> Google Colaboratory 打开 
- (也可以直接搜索谷歌colab，进入官网转到谷歌网盘) 
#### 挂载Google Drive
```python
from google.colab import drive 
drive.mount('/content/drive') 
```
	按照提示，输入一个验证码操作就好了 
- 也可以通过图形界面，直接挂载 
[![colab](http://upccaishu.top:5120/images/big/192b298f18779b7c36163519b284c739.jpg \"colab\")](http://upccaishu.top:5120/images/big/192b298f18779b7c36163519b284c739.jpg \"colab\") 
#### 设置笔记本
默认状态下，虚拟机是CPU的，无GPU，所以，要修改虚拟机配置。 
- 入口`修改-->笔记本设置-->选择GPU-->保存` 
- **为了更好使用，强烈建议，使用完成之后，把GPU改回None** 
#### 查看分配到的GPU型号 
![xPY0OO.png](https://s1.ax1x.com/2022/09/20/xPY0OO.png)
- T4还是比较好的，算力达到了6.1，和GTX1080Ti持平。比2070慢点（我在实际实验的过程中，发现T4的计算速度，要比我本地的GTX2070快，估计是散热的原因。） 
#### 友情提示 
- 由于Colab的不确定性，建议数据全部存在云盘里，而不是主机里。另外，建议模型可以保存，并且提供继续训练模型的参数接口，以方便实验可以接力跑。 
# 后记 
- CV方向属实是需要强大的Money支持，现阶段，GPU还是太贵了，租用一个月差不多就能买个30系的显卡了。学生党属实伤不起。