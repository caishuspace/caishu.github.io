---
title: "螺旋矩阵 II"
description: "力扣刷题-螺旋矩阵-【双指针、滑动窗口解题】"
keywords: "leecode,cn_59、模拟"

date: 2023-01-01T16:28:24+08:00
lastmod: 2023-01-01T16:28:24+08:00

categories:
  - 算法刷题
tags:
  - 力扣刷题
  - 数组
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
#url: "leecode-cn_59.html"
# 开启文章置顶，数字越小越靠前
# Sticky post set-top in home page and the smaller nubmer will more forward.
#weight: 1
---

力扣刷题-螺旋矩阵【模拟】

<!--more-->

#### 题目描述
给你一个正整数 n ，生成一个包含 1 到 n2 所有元素，且元素按顺时针顺序螺旋排列的 n x n 正方形矩阵 matrix 。

- 示例 1：
``` text
输入：n = 3
输出：[[1,2,3],[8,9,4],[7,6,5]]
```

- 示例 2：
``` text
输入：n = 1
输出：[[1]]
```
- 提示：
``` text
1 <= n <= 20
```

#### 代码
``` python
class Solution:
    def generateMatrix(self, n: int) -> List[List[int]]:
        ans = [[0 for _ in range(n)] for _ in range(n)]
        # ans = [[0]*n]*n   使用这个初始化会有问题，后面针对原因再做深入探讨
        top = 0
        left = 0
        right = n-1
        bottom = n-1
        ant  = 1
        
        while top < bottom:
            for i in range(left,right):
                ans[top][i]=ant
                ant+=1
            for i in range(top,bottom):
                ans[i][right] = ant
                ant +=1
            for i in range(right,left,-1):
                ans[bottom][i]= ant
                ant +=1
            for i in range(bottom,top,-1):
                ans[i][left] = ant
                ant +=1

            top+=1
            left+=1
            right-=1
            bottom-=1

        if n % 2 == 1:
            ans[n//2][n//2]=ant
        return ans
```
###### 错误记录
二维数组在初始化时会，如代码中注释的那样，会有问题，输入是`3`时，输出为：`[[8,9,5],[8,9,5],[8,9,5]]`,代码会有问题，别的也会报错，我猜测可能跟此种方式初始化的内存分配策略有关系。具体原因稍后再做探讨。