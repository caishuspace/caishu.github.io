---
title: "Eccube4.0.3安装过程"
description: "eccube4.0.3安装过程"
keywords: "eccube4.0.3安装过程"

date: 2021-07-17T18:19:09+08:00
lastmod: 2021-07-17T18:19:09+08:00

categories:
  - 技术积累
tags:
  - php
  - Eccube
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
#url: "eccube4.0.3安装过程.html"
# 开启文章置顶，数字越小越靠前
# Sticky post set-top in home page and the smaller nubmer will more forward.
#weight: 1
---

eccube4.0.3安装过程

由于开发需要，接触eccube的开发，关于eccube的内容不做详细说明，此处只作为开发过程的流程。大体而言，就是安装好PHP环境，服务器环境，以及安装好数据库。
<!--more-->


## 安装过程 
- 使用phpstudy做为集成开发环境。之前使用过xampp作为一个集成安装环境，弄了好久还是不行，后使用phpstudy；等有时间再用xampp试试。 
#### windows10系统 
- 先安装好phpstudy，下载地址：[https://www.xp.cn/](https://www.xp.cn/ \"https://www.xp.cn/\") 
- 使用Apache2.4.39,Mysql5.7.26作为服务器和数据库版本。数据库管理软件使用的phpMyAdmin4.8.5作为数据库管理软件。 
###### 安装过程
1. 新建站点，域名localhost,根目录就是网站的根目录，www下面的内容就是localhost站点 
![xPtKNd.png](https://s1.ax1x.com/2022/09/20/xPtKNd.png)
2. 创建数据库。数据库工具选择phpMyAdmin,会进入一个web站点。 
![xPtd4s.png](https://s1.ax1x.com/2022/09/20/xPtd4s.png)
- 进入站点之后，选择新建数据库，根据自己的情况写名字跟排序规则。 
![xPtB3q.png](https://s1.ax1x.com/2022/09/20/xPtB3q.png)
3. php扩展安装(如图) 
![xPt6DU.png](https://s1.ax1x.com/2022/09/20/xPt6DU.png)]
4. 下载ec-cube4的源码，放在根目录下，就行。根目录见步骤1中的根目录。 
5. 进行ec-cube4安装。ec4的安装可以按照官网提供的说明 文档进行，地址：[安装文档](https://doc4.ec-cube.net/quickstart/install \"安装文档\") 
注意几个点，在这选数据库时候，选择上面自己新建的数据库，然后初始化就可以了。 
- 备注：我按照给的官方文档，弄下来还是比较费事的，各种错误频出，大家使用的时候，应该把握一点，不要死照着教程来，知其所以依然就好---安装好mysql和服务器，而不是知其然---仅仅按照教程走一步看一步。  
#### Ubuntu20.04系统 
- ubuntu系统下，没有一个安装程序，只有一个在线的安装管理平台，使用命令`wget -O install.sh https://notdocker.xp.cn/install.sh && sudo bash install.sh` 
其安装可参考：[安装过程](https://www.xp.cn/linux.html#install-show \"安装过程\") 
- ubuntu下面安装和windows10下面大同小异，唯一区别是，其对Linux系统的支持性不太好，会出现各种bug，版本的小版本号与windows10下稍有区别。我在安装的时候，遇见的一个问题是，phpMyadmin管理打不开，所以就使用了navicat代替。这就是之气所以然的考虑。 
## 后记 
- eccube系统作为一个较为完善且庞大的系统，上手伊始是比较难顶的。我在国内的网站上，找寻相关资料十分困难，资料仅仅有那个官方的说明文档（个人觉得这文档说的比较敷衍，对新手的难度较高）。出现问题，找寻相关解决方案也几乎为0，使用google，也仅仅找到了十几条相关的内容资料。这与Java，spring boot，等拥有如烟海的解决方案大相径庭。 
- 大家如果也有相同的开发经历，可以一起探讨学习。联系方式在网站主页（Mail||Github）。
# 2021-07-17 03:48:02 星期六