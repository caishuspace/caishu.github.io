---
title: "Ubuntu20.04下修改apache2默认网站路径"
description: "Ubuntu20.04下修改apache2默认网站路径"
keywords: "Ubuntu20.04下修改apache2默认网站路径"

date: 2021-07-18T18:28:39+08:00
lastmod: 2021-07-18T18:28:39+08:00

categories:
  - 问题解决
tags:
  - Ubuntu
  - Linux
  - apache2
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
#url: "ubuntu20.04下修改apache2默认网站路径.html"
# 开启文章置顶，数字越小越靠前
# Sticky post set-top in home page and the smaller nubmer will more forward.
#weight: 1
---

Ubuntu20.04下修改apache2默认网站路径

<!--more-->

## 原因\r\n- 路径下会出现权限问题，每次保存都输入密码，所以修改路径到个人用户路径下
- 本着避免不交代环境只交代怎么做的流氓行为，先交代一下环境问题。本文是在Ubnutu20.04,apahce2环境下进行的修改。
## 过程
1. 修改文件`/etc/apache2/apache2.config`，找到如下代码块
```html
<dirctory /var/www> //把此处路径修改为自己的路径	
options····
	···
  ···
</dirctory>
```
2. 修改文件`/etc/aapche2/sites-enabled/000default.conf`,找如下代码，将路径修改为自己的
```html
DocumentRoot /usr/local/www/data
```
此外在下面新增一部分代码（不然会出现403错误）
```html
<directory "/usr/local/www/data\"> //此处将路径修改为自己的    
  
  Options Indexes FollowSymLinks
      AllowOverride None
      Order allow,deny
      Allow from all
  </directory>
  ```
