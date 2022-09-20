---
title: "在服务器上部署Jupyter"
description: "在服务器上部署Jupyter"
keywords: "在服务器上部署Jupyter"

date: 2020-12-04T16:32:00+08:00
lastmod: 2020-12-04T16:32:00+08:00

categories:
  - 问题解决
tags:
  - jupyter
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
#url: "在服务器上部署jupyter.html"
# 开启文章置顶，数字越小越靠前
# Sticky post set-top in home page and the smaller nubmer will more forward.
#weight: 1
---

在服务器上部署Jupyter
服务器安装jupyter
今天手边没有自己的电脑，但是想要编程，虽然有着很多的在线编程网站，但是在写python代码的时候，一些库没有，很恼火，但是又不能乱搞别人的电脑，就想起了搞一搞jupyter。目前看起来效果还不错。

<!--more-->

## 前言 
- Jupyter Notebook是一个交互式笔记本，可以用来写python脚本或者markdown语言，部署在浏览器之后，可以通过浏览器在线编程，实时运行python脚本。 
## 安装流程 
- 环境：python3+Centos8+ipython 
- 我是通过下载Anaconda顺便安装了jupyter。大家也可以直接通过yum、apt-get等包管理工具进行下载安装。安装之前，要确保平台已经安装好了python3环境。 
#### 安装Anaconda 
- 获取安装包 `wget  https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/Anaconda3-5.0.1-Linux-x86_64.sh` 
- 安装命令 `sh Anaconda3-5.0.1-Linux-x86_64.sh ` 一路yes就可以了 
- 配置环境变量，有多种方式，我用的是 
1. `vi /etc/profile`   
2. `export PATH=~/anaconda3/bin:$PATH` 
- 更新环境变量 `source /etc/profile`
- 其它配置方式：https://www.linuxprobe.com/environment-variable-configuration.html 
- 检查版本`conda -V`
[![xPuabq.png](https://s1.ax1x.com/2022/09/20/xPuabq.png)]

如果出现图中效果，证明安装成功 
## 配置jupyter
- 生成配置文件`jupyter notebook --generate-config`  
- 路径在：`~/.jupyter/jupyter_notebook_config.py`
- 进入python环境，如图
[![xPuzi8.png](https://s1.ax1x.com/2022/09/20/xPuzi8.png)]
注意复制好里面的out[2]部分，后面配置文件要用。
- 编辑jupyter配置文件
`vi /root/.jupyter/jupyter_notebook_config.py`
- 修改以下条目【注意去掉#】
```python
c.NotebookApp.ip = \'*\' 
# 设置Jupyter监听的ip地址，修改为*表示监听所有ip地址
c.NotebookApp.password = u\'' 
# 将该内容替换为上一步设置密码时生成的sha1值AAc.NotebookApp.open_browser = False 
# 禁止启动时自动打开浏览器(本来在桌面平台上安装使用时可以开启，在服务器上不需要此设置，因此设置为False)AAc.NotebookApp.port = 1024 
# 指定访问的端口，按照自己喜好设定，默认是8888，注意不要和已用端口冲突AAc.NotebookApp.notebook_dir = \'/Your/Directory\' 
# 设置运行时的目录，因为以root身份运行时默认会在/root目录下，因此最好修改成自己喜欢的目录，例如\'/home/jupyter\'AA```AAAA- 上步骤中，运行目录必须已经存在，否则会启动失败，自己手动创建即可。

```
- 启动

```python
jupyter notebook --no-browser --allow-root 
```
- 我这里加入--allow-root是因为我是以root身份运行的，如果不添加就无法启动，非root用户启动时可以不加
- 接下来打开浏览器就可以看到了\"http://ip：端口\"

