---
title: "How_to_start_article_use_hugo"
description: "how_to_start_article_use_hugo"
keywords: "how_to_start_article_use_hugo"

date: 2022-12-22T19:29:19+08:00
lastmod: 2022-12-22T19:29:19+08:00

categories:
  - 其他
tags:
  - 博客写作
  - hugo使用
# categories:技术积累、论文阅读、问题解决、算法刷题、其他等四个条目，其余放在tags里面。

# 原文作者
# Post's origin author name
#author:
# 原文链接
# Post's origin link URL
link: https://www.gohugo.org/
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
#url: "how_to_start_article_use_hugo.html"
# 开启文章置顶，数字越小越靠前
# Sticky post set-top in home page and the smaller nubmer will more forward.
#weight: 1
---

开始写作一个文章【以跳过hugo安装等过程】

<!--more-->

## 开始写作一个文章
#### 本地打开hugo服务,以实时预览的模式
``` bash
hugo server --buildDrafts
```
#### 新建一个文件
``` bash
hugo new /post/子路径/文件名.md
```
- 例如：
`hugo new /post/pre/how_to_start_article_use_hugo.md`

#### 生成静态文件
- 必须在根目录下进行【我使用的主题是hugo-theme-next】
``` bash 
hugo -t hugo-theme-next
``` 

#### 托管到GitHub上
``` bash 
git add .
git commit -m "message"
git push  
```

###### 后记
- 长时间不写博客，手生了，记录一下过程。