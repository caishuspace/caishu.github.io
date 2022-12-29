---
title: "长度最小的子数组"
description: "力扣刷题-长度最小的子数组-【双指针、滑动窗口解题】"
keywords: "leetcode,cn_209"

date: 2022-12-29T12:32:22+08:00
lastmod: 2022-12-29T12:32:22+08:00

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
link: https://leetcode.cn/problems/minimum-size-subarray-sum/
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
#url: "leetcode-cn_209.html"
# 开启文章置顶，数字越小越靠前
# Sticky post set-top in home page and the smaller nubmer will more forward.
#weight: 1
---

力扣刷题-长度最小的子数组

<!--more-->
#### 题目描述
给定一个含有 n 个正整数的数组和一个正整数 target 。

找出该数组中满足其和 ≥ target 的长度最小的 连续子数组 [numsl, numsl+1, ..., numsr-1, numsr] ，并返回其长度。如果不存在符合条件的子数组，返回 0 。

- 示例1
``` text
输入：target = 7, nums = [2,3,1,2,4,3]
输出：2
解释：子数组 [4,3] 是该条件下的长度最小的子数组。
```
- 示例2
``` text
输入：target = 4, nums = [1,4,4]
输出：1
```
- 示例3
``` text
输入：target = 11, nums = [1,1,1,1,1,1,1,1]
输出：0
``` 
- 提示
``` text
1 <= target <= 109
1 <= nums.length <= 105
1 <= nums[i] <= 105
```

#### 代码
``` python
class Solution:
    def minSubArrayLen(self, target: int, nums: List[int]) -> int:
        l = len(nums)
        left = 0 
        flag = True
        minlen = 1e5+1
        sum = 0
        for i in range(0,l):
            sum += nums[i]

            while sum >= target:
                flag = False
                sum = sum - nums[left]
                minlen = min(minlen,i-left+1)
                left+=1
        if flag:
            return 0
        return  minlen       
```