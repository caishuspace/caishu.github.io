---
title: "Eccube4（插件开发三）"
description: "Eccube4（插件开发三）"
keywords: "Eccube4（插件开发三）"

date: 2021-08-11T18:53:16+08:00
lastmod: 2021-08-11T18:53:16+08:00

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
#url: "eccube4（插件开发三）.html"
# 开启文章置顶，数字越小越靠前
# Sticky post set-top in home page and the smaller nubmer will more forward.
#weight: 1
---

Eccube4（插件开发三）
CSV文件DOM头引起的编码问题。
CSV直接用Excel打开，乱码问题解决。

<!--more-->
## 前言
- 有个任务，针对导出csv文件，直接Excel打开乱码编程语言是PHP。
- BOM(byte-order mark，字节顺序标记)，详细可百度。
# 乱码根源
- 学计算机的应该童鞋们，应该很清晰，乱码问题，那就是编码不对嘛，找到正确的编码，就好了。（之前从未想过有一天会栽在编码问题上，之前一般是系统切换，才会导致这种问题）。
## 原因
- PHP程序默认导出CSV编码方式，是UTF-8，还是不带BOM头，也叫万国码。具体不赘述。而本地Excel（简体中文环境下）默认使用的GB2321编码方式（也有网友说是Ascii编码，是什么不重要，知道两个编码方式不一样就对了）。
- 在没有BOM头的文件中，默认打开方式的编码是Excel的编码方式。
## 问题解决方案一（针对用户，治标）
 office-2019
 - 利用ofice-Excel表格的数据导入功能，导入文件时候，源文件编码记得选UTF-8，然后导入数据即可。
 ## 问题解决方案二（针对程序员，治本）
 - 直接在程序上，生成文件时，添加BOM头。\r\n- 缺少的BOM头`xEFxBBxBF`
 - 直接把上述DOM添加到文章开头即可，就是文件读写的时候。
 ## 后记
 - 结果就加了一行代码，过程整了一下午