---
title: "四数相加 II"
description: "454. 四数相加 II，利用哈希表解题"
keywords: "leecode,cn_454"

date: 2023-02-07T21:07:18+08:00
lastmod: 2023-02-07T21:07:18+08:00

categories:
  - 算法刷题
tags:
  - 力扣刷题
  - 哈希表
# categories:技术积累、论文阅读、问题解决、算法刷题、其他等四个条目，其余放在tags里面。

# 原文作者
# Post's origin author name
#author:
# 原文链接
# Post's origin link URL
link: https://leetcode.cn/problems/4sum-ii/
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
#url: "leecode-cn_454.html"
# 开启文章置顶，数字越小越靠前
# Sticky post set-top in home page and the smaller nubmer will more forward.
#weight: 1
---

454. 四数相加 II，利用哈希表解题

<!--more-->

#### 问题描述
给你四个整数数组 nums1、nums2、nums3 和 nums4 ，数组长度都是 n ，请你计算有多少个元组 (i, j, k, l) 能满足：

0 <= i, j, k, l < n
nums1[i] + nums2[j] + nums3[k] + nums4[l] == 0

用例描述：
```
示例1：
输入：nums1 = [1,2], nums2 = [-2,-1], nums3 = [-1,2], nums4 = [0,2]
输出：2
解释：
两个元组如下：
1. (0, 0, 0, 1) -> nums1[0] + nums2[0] + nums3[0] + nums4[1] = 1 + (-2) + (-1) + 2 = 0
2. (1, 1, 0, 0) -> nums1[1] + nums2[1] + nums3[0] + nums4[0] = 2 + (-1) + (-1) + 0 = 0

示例2 ：
输入：nums1 = [0], nums2 = [0], nums3 = [0], nums4 = [0]
输出：1

提示：
n == nums1.length
n == nums2.length
n == nums3.length
n == nums4.length
1 <= n <= 200
-228 <= nums1[i], nums2[i], nums3[i], nums4[i] <= 228

```
#### 代码
- 首先定义 一个字典【哈希表】，key放a和b两数之和，value 放a和b两数之和出现的次数。
- 遍历nums1和nums2数组，统计两个数组元素之和，和出现的次数，放到map中。
- 定义int变量count，用来统计 a+b+c+d = 0 出现的次数。
- 在遍历nums3和nums4数组,求和，找到如果 0-(c+d) 在map中出现过的话，就用count把map中key对应的value也就是出现次数统计出来。
- 最后返回统计值 count 就可以了

```python
class Solution:
    def fourSumCount(self, nums1: List[int], nums2: List[int], nums3: List[int], nums4: List[int]) -> int:

        dic = {}

        for i in nums1:
            for j in nums2:
                sum = i + j 
                if sum in dic.keys():
                    dic[sum]+=1
                else:
                    dic[sum] = 1
        
        ans = 0

        for i in nums3:
            for j in nums4:
                sum1 = -(i+j)
                if sum1 in dic.keys():
                    ans+=dic[sum1]
        
        return ans
```