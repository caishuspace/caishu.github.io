---
title: "配置nginx服务器小结"
description: "配置nginx服务器小结"
keywords: "配置nginx服务器小结"

date: 2021-03-29T17:58:51+08:00
lastmod: 2021-03-29T17:58:51+08:00

categories:
  - 技术积累
tags:
  - nginx
  - 服务器
  - Linux
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
#url: "配置nginx服务器小结.html"
# 开启文章置顶，数字越小越靠前
# Sticky post set-top in home page and the smaller nubmer will more forward.
#weight: 1
---

配置nginx服务器小结

<!--more-->

## 一些常用命令 
```text
ps -ef | grep nginx  查看nginx安装目录 
nginx -t 查看配置文件nginx.conf路径 
nginx 安装目录 -c nginx.com  配置文件沐目录，参数-c指定配置文件路径，不加默认加载其安装目录的conf子目录中的nginx.conf文件 
nginx -参数 
Nginx 的参数包括： 
-c <path_to_config>：使用指定的配置文件而不是 conf 目录下的 nginx.conf 。 
-t：测试配置文件是否正确，在运行时需要重新加载配置的时候，此命令非常重要，用来检测所修改的配置文件是否有语法错误。    
-v：显示 nginx 版本号。    
-V：显示 nginx 的版本号以及编译环境信息以及编译时的参数。        
start nginx : 启动nginx    
nginx -s reload ：修改配置后重新加载生效    
nginx -s reopen ：重新打开日志文件        
关闭nginx：    
nginx -s stop : 快速停止nginx    
nginx -s quit ：完整有序的停止nginx            
问题描述：执行 nginx -t 是OK的，然而在执行 nginx -s reload 的时候报错    　　　　
nginx: [error] invalid PID number “” in “/run/nginx.pid”    
解决办法    　　　　
需要先执行    　　　　
nginx -c /etc/nginx/nginx.conf        
netstat -pan | grep 80 查看端口号		
## 安装配置nginx服务器
#### 安装
- 我采用的pip直接安装，大家也可以采用下载源码自行编译安装。
`pip install ngnix`
```
#### 查看安装位置
- pip安装 之后，有可能会出现找不到conf配置文件的问题，大家可以使用命令查看：
- `ps -ef | grep nginx` 查看ngnix安装目录- `ngnix -t`查看ngnix.conf路径
#### 修改ngnix文件
- 我是配置ngnix的反向代理，具体的反向代理配置，可以自行百度进行解决。
- 反向代理的时候，注意一个坑，一个关于斜杠`/`的问题。
#### 启动ngnix
- `ngnix -t` 显示`nginx: the configuration file /etc/nginx/nginx.conf syntax is oknginx: configuration file /etc/nginx/nginx.conf test is successful`
说明配置文件没错。
- `ngnix -c /etc/nginx/nginx.conf` 加载配置文件。（如果不执行会报错`nginx: [error] invalid PID number “” in “/run/nginx.pid”`,具体原因 ，暂未知）
- `nginx -s reload` 重新载入配置生效
#### 可能出现的问题
- 一个是上面提到的`nginx: [error] invalid PID number “” in “/run/nginx.pid”` 解决方案在上面。
- 另一个是映射端口被占用`nginx: [emerg] bind() to 0.0.0.0:80 failed (98: Address already in use)` ,这时候可以查看一下端口具体被那些应用占用，通过`
netstat -pan | grep 端口号`查看，并使用`kill -9 端口号`消灭该端口号。
