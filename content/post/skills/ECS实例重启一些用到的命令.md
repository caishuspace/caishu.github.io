---
title: "ECS实例重启一些用到的命令"
description: "ECS实例重启一些用到的命令"
keywords: "ECS实例重启一些用到的命令"

date: 2020-10-21T14:55:43+08:00
lastmod: 2020-10-21T14:55:43+08:00

categories:
  - 技术积累
tags:
  - Linux
  - 数据库
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
#url: "ecs实例重启一些用到的命令.html"
# 开启文章置顶，数字越小越靠前
# Sticky post set-top in home page and the smaller nubmer will more forward.
#weight: 1
---

ECS实例重启一些用到的命令

<!--more-->

## 数据库（8.0）
 - 查看状态`service mysqld status`
 - 启动数据库`service mysqld start`
 - 关闭数据库`service mysqld stop`
 ## 启动jar包服务
 - 后台运行jar包服务`nohup java -jar XXX.jar &`
 ## 关闭jar包服务
 - 查看服务端口号`ps -ef |grep XXX.jar`
 - 关掉服务进程`kill 9 端口号`

>记录服务器重启和服务重启

