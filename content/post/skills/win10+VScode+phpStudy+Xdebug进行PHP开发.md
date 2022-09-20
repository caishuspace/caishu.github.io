---
title: "Win10+VScode+phpStudy+Xdebug进行PHP开发"
description: "win10+VScode+phpStudy+Xdebug进行PHP开发"
keywords: "win10+VScode+phpStudy+Xdebug进行PHP开发"

date: 2021-07-26T18:32:47+08:00
lastmod: 2021-07-26T18:32:47+08:00

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
#url: "win10+vscode+phpstudy+xdebug进行php开发.html"
# 开启文章置顶，数字越小越靠前
# Sticky post set-top in home page and the smaller nubmer will more forward.
#weight: 1
---

win10+VScode+phpStudy+Xdebug进行PHP开发

<!--more-->

## 准备工作 
- 安装好VScode+phpstudy，很简单，基本都是一路next。 
- phpstudy是一个很好的php环境集成工具，新手建议使用，为了自己加深理解，可以自己安装环境。 
- vscode是一个轻量级的编辑器，可以用来书写各种语言，拥有强大的插件库。 
## 配置过程 
#### php语言设置 
- 使用phpstudy安装好apache或者nginx，数据库,并安装好自己需要的PHP版本。（其实开发阶段，可以只安装php+数据库即可，在运行部署的时候使用apache或者ngnix） 
- VsCode安装插件`PHP Debug`,`PHP Intelephense`,`PHP ointellisense for codeigniter`,`PHP Server`,`PHP Xdebug`等 
- php.ini配置文件（使用phpstudy启用Xdebug，自动生成的配置信息）  
```text 
[Xdebug] 
zend_extension=G:/phpstudy_pro/Extensions/php/php7.3.4nts/ext/php_xdebug.dll 
xdebug.collect_params=1 
xdebug.collect_return=1 
xdebug.auto_trace=Off 
xdebug.trace_output_dir=G:/phpstudy_pro/Extensions/php_log/php7.3.4nts.xdebug.trace 
xdebug.profiler_enable=Off 
xdebug.profiler_output_dir=G:/phpstudy_pro/Extensions/php_log/php7.3.4nts.xdebug.profiler 
xdebug.remote_enable=on 
xdebug.remote_autostart = on 
xdebug.remote_host=localhost 
xdebug.remote_port=900
xdebug.remote_handler=dbgp 
 ``` 
- 补充一句，php.ini中启用Xdebug插件，如果使用phpstudy的话，直接在控制面板里启用Xdebug即可。从网上自己找配置文件也可以（此处仅作为一个提醒）。 
- 语言最后一点，很重要！！！要把php的路径放入环境变量里，不然会报错（这里的路径只到php.exe的上级目录即可，也就是目录里不包含这个文件名，否则会报错） 
 [![php报错](http://upccaishu.top:5120/images/big/9662469bcc72ca6f834cebcb9da5918a.png \"php报错\")](http://upccaishu.top:5120/images/big/9662469bcc72ca6f834cebcb9da5918a.png \"php报错\") 
 ## VsCode配置 
#### setting.json文件 
 
- `设置->扩展->PHP->setting.json`文件,具体内容如下： 
``` text
{ 
"php.validate.executablePath\": \"G:/phpstudy_pro/Extensions/php/php7.3.4nts/php.exe\",     
"phpserver.port\": 9000,     \"phpserver.phpConfigPath\": \"G:\\\\phpstudy_pro\\\\Extensions\\\\php\\\\php7.3.4nts\\\\php.ini\", 
"phpserver.phpPath\": \"G:\\\\phpstudy_pro\\\\Extensions\\\\php\\\\php7.3.4nts\\\\php.exe\", 
} 
``` 
#### launch.json 
- `运行->打开配置` 
``` text
{ 
// 使用 IntelliSense 了解相关属性。  
// 悬停以查看现有属性的描述。 
// 欲了解更多信息，请访问: https://go.microsoft.com/fwlink/?linkid=830387 
\"version\": \"0.2.0\",
\"configurations\": [
  { 
    "name\": \"Listen for Xdebug\",
    \"type\": \"php\", 
    \"request\": \"launch\",
    \"port\": 9000
    } 
    ] 
} 
``` 
## 写在最后 QQQQ - 程序能跑起来，就千万别动！！！！无论程序是以什么情况跑起来的！好奇心不要太强，尤其是DDL逼近的时候，不然会十分头疼！ 