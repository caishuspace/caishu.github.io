---
title: "977.有序数组的平方"
description: "力扣刷题-有序数组的平方-【双指针法】"
keywords: "leetcode,cn_977"

date: 2022-12-27T20:37:49+08:00
lastmod: 2022-12-27T20:37:49+08:00

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
link: https://leetcode.cn/problems/squares-of-a-sorted-array/
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
#url: "leetcode-cn_977.html"
# 开启文章置顶，数字越小越靠前
# Sticky post set-top in home page and the smaller nubmer will more forward.
#weight: 1
---

力扣刷题-有序数组的平方【使用双指针法，O(n)的时间复杂度解题】

<!--more-->

#### 问题描述
给你一个按 非递减顺序 排序的整数数组 nums，返回 每个数字的平方 组成的新数组，要求也按 非递减顺序 排序。
- 示例 1：
``` text
输入：nums = [-4,-1,0,3,10]
输出：[0,1,9,16,100]
解释：平方后，数组变为 [16,1,0,9,100]
排序后，数组变为 [0,1,9,16,100]
```

- 示例 2：
``` text
输入：nums = [-7,-3,2,3,11]
输出：[4,9,9,49,121]
```

- 提示
``` text
1 <= nums.length <= 104
-104 <= nums[i] <= 104
nums 已按 非递减顺序 排序
```

#### 代码
- 解题思路：给定的数字是有序的，所以，最大的数字肯定在两端，新开一个数组，从大到小开始存储序列。
- 一开始的思路是找最接近零的，从小到大去挨个寻找，得先找到绝对值最小的数字，本身就是一个耗费时间的步骤，所以，反其道而行之，找最大的开始也是一样的，因为最大的平方数是两端，这点是确定的。

``` python
class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        l = len(nums)
        li = [0]*l
        left = 0 
        rigt = l -1
        l=l-1
        while(l>=0):
            if nums[left]**2 >= nums[rigt]**2:
                li[l]=nums[left]**2
                left+=1
            else:
                li[l]=nums[rigt]**2
                rigt-=1
            l-=1
        return li
```

