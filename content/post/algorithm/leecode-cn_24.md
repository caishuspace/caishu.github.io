---
title: "24. 两两交换链表中的节点 Cn_24"
description: "leecode-cn_24  两两交换链表中的节点"
keywords: "leecode,cn_24 两两交换链表中的节点"

date: 2023-01-05T18:27:12+08:00
lastmod: 2023-01-05T18:27:12+08:00

categories:
  - 算法刷题
tags:
  - 力扣刷题
  - 链表
# categories:技术积累、论文阅读、问题解决、算法刷题、其他等四个条目，其余放在tags里面。

# 原文作者
# Post's origin author name
#author:
# 原文链接
# Post's origin link URL
link: https://leetcode.cn/problems/swap-nodes-in-pairs/
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
#url: "leecode-cn_24.html"
# 开启文章置顶，数字越小越靠前
# Sticky post set-top in home page and the smaller nubmer will more forward.
#weight: 1
---

24. 两两交换链表中的节点
- 其实和交换两相邻的数字方法无二，只不过要多记录两个节点 以及上下节点的位置关系。【画个图会方便捋清楚】

<!--more-->

#### 问题描述
给你一个链表，两两交换其中相邻的节点，并返回交换后链表的头节点。你必须在不修改节点内部的值的情况下完成本题（即，只能进行节点交换）。
- 示例 1：
``` text
输入：head = [1,2,3,4]
输出：[2,1,4,3]
```
- 示例 2 ：
``` text
输入：head = []
输出：[]
```
-示例 3：
``` text
输入：head = [1]
输出：[1]
````
###### 提示
链表中节点的数目在范围 [0, 100] 内
0 <= Node.val <= 100

#### 代码
``` python
# @lc code=start
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def swapPairs(self, head: Optional[ListNode]) -> Optional[ListNode]:
        h1 = ListNode(next=head)
        h = h1
        
        while h.next !=None and h.next.next!=None:
            p = h.next  // 记录临时节点
            q = h.next.next.next  // 记录临时节点
            h.next = h.next.next
            h.next.next = p
            h.next.next.next= q

            h = h.next.next

        return h1.next
```