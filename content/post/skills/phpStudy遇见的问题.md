---
title: "PhpStudy遇见的问题"
description: "phpStudy遇见的问题"
keywords: "phpStudy遇见的问题"

date: 2021-07-16T18:15:06+08:00
lastmod: 2021-07-16T18:15:06+08:00

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
#url: "phpstudy遇见的问题.html"
# 开启文章置顶，数字越小越靠前
# Sticky post set-top in home page and the smaller nubmer will more forward.
#weight: 1
---

phpStudy遇见的问题


由于项目需要学习ec-cube开发，前期使用xampp配置了好半天，分开环境是明明白白的了，但是项目仍然起步不了，后来，转到Ubuntu下进行开发，仍然问题一箩筐。后来，在项目负责人的指导下，使用phpstudy集成工具进行开发，将环境在win下安装成功。于是我考虑使用Ubuntu重新走一遍流程。
<!--more-->
## 问题描述
- 在安装phpstudy时候，启动apache2,发现报错如下：
![xPYO10.png](https://s1.ax1x.com/2022/09/20/xPYO10.png)
## 解决方案
- 问题百度的时候，有很多方案，大概就是端口占用，但是我操作下来，还是不行。后来还找到一个问题描述，是配置文件的端口号冲突。
- 在本来的Ubuntu系统中，使用apt安装了一个apache2,占用了80端口，将Ubuntu系统下的apache2关掉，使用phpstudy下的集成apache环境即可。
- 使用`service apache2 stop`停止掉系统下的apache2,再使用phpstudy下的apache2启动，问题解决。## 一些命令
- `service apache2 start`启动apache2服务
- `service apache2 stop`停止服务
- `service apache2 restart`重启apache2服务## 写在最后
- 时隔多日，再次写下博客，下次应该就得考虑服务器迁移问题了。 2021-07-16 21:34:33 星期五