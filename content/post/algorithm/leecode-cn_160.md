---
title: "面试题 链表相交 160"
description: "leecode-cn_160"
keywords: "leecode,cn_160"

date: 2023-01-08T20:04:40+08:00
lastmod: 2023-01-08T20:04:40+08:00

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
link: https://leetcode.cn/problems/intersection-of-two-linked-lists-lcci/
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
#url: "leecode-cn_160.html"
# 开启文章置顶，数字越小越靠前
# Sticky post set-top in home page and the smaller nubmer will more forward.
#weight: 1
---

面试题 02.07. 链表相交-双节点思路
<!--more-->
#### 题目描述
给你两个单链表的头节点 headA 和 headB ，请你找出并返回两个单链表相交的起始节点。如果两个链表没有交点，返回 null 。
图示两个链表在节点 c1 开始相交：
- ![](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/14/160_statement.png)
题目数据 保证 整个链式结构中不存在环。

注意，函数返回结果后，链表必须 保持其原始结构 。

示例 1：
![](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/14/160_example_1.png)
``` text
输入：intersectVal = 8, listA = [4,1,8,4,5], listB = [5,0,1,8,4,5], skipA = 2, skipB = 3
输出：Intersected at '8'
解释：相交节点的值为 8 （注意，如果两个链表相交则不能为 0）。
从各自的表头开始算起，链表 A 为 [4,1,8,4,5]，链表 B 为 [5,0,1,8,4,5]。
在 A 中，相交节点前有 2 个节点；在 B 中，相交节点前有 3 个节点。
```
示例 2：
![](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/14/160_example_2.png)
``` text
输入：intersectVal = 2, listA = [0,9,1,2,4], listB = [3,2,4], skipA = 3, skipB = 1
输出：Intersected at '2'
解释：相交节点的值为 2 （注意，如果两个链表相交则不能为 0）。
从各自的表头开始算起，链表 A 为 [0,9,1,2,4]，链表 B 为 [3,2,4]。
在 A 中，相交节点前有 3 个节点；在 B 中，相交节点前有 1 个节点。
```
示例 3：
![](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/14/160_example_3.png)
``` text
输入：intersectVal = 0, listA = [2,6,4], listB = [1,5], skipA = 3, skipB = 2
输出：null
解释：从各自的表头开始算起，链表 A 为 [2,6,4]，链表 B 为 [1,5]。
由于这两个链表不相交，所以 intersectVal 必须为 0，而 skipA 和 skipB 可以是任意值。
这两个链表不相交，因此返回 null 。
```
#### 代码
- 我们求出两个链表的长度，并求出两个链表长度的差值，然后让curA移动到，和curB 末尾对齐的位置。此时我们就可以比较curA和curB是否相同，如果不相同，同时向后移动curA和curB，如果遇到curA == curB，则找到交点。
``` python

# @lc code=start
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def getIntersectionNode(self, headA: ListNode, headB: ListNode) -> Optional[ListNode]:
        h1 = ListNode(next = headA)
        h2 = ListNode(next = headB)

        cur1 = h1.next
        cur2 = h2.next
        cnt1 = 0
        cnt2 = 0
        while cur1 != None:
            cnt1 +=1
            cur1 = cur1.next
        
        while cur2 != None:
            cnt2 +=1
            cur2 = cur2.next
        curA = h1.next
        curB = h2.next
        
        if cnt1 >=cnt2:
            for i in range(0,cnt1-cnt2):
                curA = curA.next
        else:
            for i in range(0,cnt2-cnt1):
                curB = curB.next  
               
        while curA!=None:
            if curA == curB:
                return curA
            curA = curA.next
            curB = curB.next
        return None
``` 