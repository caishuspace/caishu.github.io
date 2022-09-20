---
title: "Eccube4（插件开发二）"
description: "Eccube4（插件开发二）"
keywords: "Eccube4（插件开发二）"

date: 2021-08-08T18:49:24+08:00
lastmod: 2021-08-08T18:49:24+08:00

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
#url: "eccube4（插件开发二）.html"
# 开启文章置顶，数字越小越靠前
# Sticky post set-top in home page and the smaller nubmer will more forward.
#weight: 1
---

Eccube4（插件开发二）
## 多级折叠菜单
－这更偏向于经验贴，而不是技术贴。
<!--more-->


#### 前面
- 本意是想实现一个Tree，但是这个Tree从某种程度上来说是十分简单的，但同时想要做好，却又是十分艰难的。在一些现在比较主流的前端UI框架里，大多有此类型的树形控件（本人不怎么接触前端，了解有限）
比如[[框架]ant design ][https://ant.design/components/tree-cn/]。github上，也有此类插件可引用，但是大多数都是属于那种自己构建Json数据，然后利用JS对DOM进行操作。
[https://ant.design/components/tree-cn/]: https://ant.design/components/tree-cn/ \"Ant Design of Vue\"

- 本来的思路，使用JS重新构建JSON数据，然后套用插件，结果无奈，被迫放弃了这个思路。因为引入一个新的框架，成本开销还是比较大的，其实是在已经使用一个框架的前提下。
－后来改变思路，想使用自己写的JS+HTML+CSS封装一下，来对DOM进行操作，写自己的Tree，后来也放弃了。原因是，由于原框架了解少，牵一发而动全身，工作量会越走越大。无奈，最后，只能是在原来的内容上修修改改。所幸，最后成功了。
#### 敲代码是快乐的，但思考的过程是痛苦的
-当不会的时候，是困难的，当熟悉了之后吗，简单了。
- 最后的代码实现，其实只有几十行的代码量。得益于舍友的提示，最后改了个方式-----**-数据可以有，我看不见你，你不就没有了？**
- 使用`dissplay`属性，或者`hide`和`show`方法，可以实现树形结构的隐藏和出现！
- 其他就是分析你的数据标签结构，然后解析DOM节点，有针对性地进行展开折叠就好了。
- 个人针对个人特殊情况写的，没有普遍性，没有代码参考价值，思想还是可以的（也有可能是这种思维早就有，但是，本人接触前端开发少，所以产生的错觉。（其实有一本书，描述方式时，曾经利用过这中display属性进行前端的这种数据通信））（朋友也曾在公司的业务中，用过这种思维方式，也被上司采纳了！）
## 后记
- 这次深切让我预习复习了前端相关内容知识啊，被打击的不行，这知识海洋差点给淹死~ 