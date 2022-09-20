---
title: "Eccube4（插件开发一）"
description: "Eccube4（插件开发一）"
keywords: "Eccube4（插件开发一）"

date: 2021-07-29T18:40:52+08:00
lastmod: 2021-07-29T18:40:52+08:00

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
#url: "eccube4（插件开发一）.html"
# 开启文章置顶，数字越小越靠前
# Sticky post set-top in home page and the smaller nubmer will more forward.
#weight: 1
---

Eccube4（插件开发一）


因为本人也是刚开始接触这个东西，有何不对之处还望批评指正。
<!--more-->

## 何为Eccube4 
- 至于Eccube4是啥，感兴趣的可以去百度了。从技术角度，就是一个网站，一个类似框架的网站，可供开发人员自行扩充的网站。个人觉得，说Eccube是个网站，不如说它是个框架，一个电商平台的框架。 
- 平心而论，这个网站规模是比较庞大的，从目前的接触来说，该网站主题使用了PHP作为建站语言，其文件组织结构类似Symofony，当然，其开发也是使用Symfony框架开发此网站。其前端模板引擎使用了twig，至于这个twig是啥，我目前也是一知半解,用程序员的话说，这就是一个模板引擎，和thymeleaf，jsp差不多。至于twig的用法，可以参考网站https://twig.symfony.com/doc/3.x/ 
也可自行查找汉化网站。
- 其实新入门一个内容，不害怕新，但是害怕没有成熟的生态和详尽的说明文档，依靠试错是很麻烦并且费事的。目前，国内的IT环境搜索Eccube的内容比较少，在V2EX上有零星的介绍，所以，可以去雅虎搜索一下，内容稍微多点，并且详细点,毕竟雅虎是日本的X度，也可以具体怎么去搜索，那就自己去摸索了，毕竟茶水不是那么好喝的。 
## Plugin 插件开发 
- 先声明：我虽然这么干了，但是标准流程未必是这么走的。
#### 先说点废话 
- 一开始，我也是蛮好奇这个插件怎么开发的，毕竟那些插件的模板样例，都是一个压缩文件，解压之后的目录结构类似于Symfony创建项目的文件目录结构。所以开始，我是有着两个猜想的，一个是，直接构建目录，完成功能之后，打包压缩，但是吧，这样操作也存在显而易见的问题，就是，你凭什么让你的Plugin跟原网站结合？另一个猜想就是，在文件的目录下面创建Symfony项目，作为一部分进行开发。 
- 很不幸运，这两个方式都是错的。下面开始说正确的插件开发流程。 
 #### 上正餐
 - 开发其实是使用Eccube的bin/console命令进行创建Plugin骨架，这也是为什么我前面觉得Eccube更像一个矿建的原因。 
 - **创建插件** 
1. `php bin/console eccube:plugin:generate`
2. `php bin/console e:p:g` 
以上两个命令均可 
![xPN4oQ.png](https://s1.ax1x.com/2022/09/20/xPN4oQ.png)
- **安装插件**
1. `php bin/console eccube:plugin:install --code=upccaishu`[上面创建的code名称，作为plugin的唯一标识，在一个项目里，具有唯一性]
2. `php bin/console e:p:i`
![xPNoJs.png](https://s1.ax1x.com/2022/09/20/xPNoJs.png)
- **激活插件**
1. `php bin/console eccube:plugin:enable`
2. `php bin/console e:p:e`
![xPN7zq.png](https://s1.ax1x.com/2022/09/20/xPN7zq.png)
- 具体详细内容，感兴趣的可以联系我一起学习，以上就是搭建Plugin的空壳子，空壳子搭建简单，但是找寻资料是真的头秃。上网找相关资料，都能找到公司。找不到博客，也说明了问题。
## 临时任务
- debug- 跟一个应该差不多同龄的哥们一块找bug，找Eccube的bug，目前已经定位到了出错的原因和直接出错的地方，但是修改真的，还没有头绪，毕竟，内容还没看完理解好，就去找别人的bug，有那么亿点点难。害怕涉及比较隐私的地方，所以不详细说了。
- 不得不说，运维的时候，就体现出来规范开发的必要性！！！
