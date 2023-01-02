---
title: "反转链表"
description: "力扣刷题-反转链表-【双指针】"
keywords: "leecode,cn_206"

date: 2023-01-02T16:01:58+08:00
lastmod: 2023-01-02T16:01:58+08:00

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
link: https://leetcode.cn/problems/reverse-linked-list/
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
#url: "leecode-cn_206.html"
# 开启文章置顶，数字越小越靠前
# Sticky post set-top in home page and the smaller nubmer will more forward.
#weight: 1
---

反转链表-力扣刷题-双指针

<!--more-->
#### 问题描述
- 给你单链表的头节点 head ，请你反转链表，并返回反转后的链表。
- 示例 1：
``` text
输入：head = [1,2,3,4,5]
输出：[5,4,3,2,1]
```
``` text
- 示例2：
输入：head = [1,2]
输出：[2,1]
```
``` text
- 示例3：
输入：head = []
输出：[]
```
``` text
- 提示
链表中节点的数目范围是 [0, 5000]
-5000 <= Node.val <= 5000
```
进阶：链表可以选用迭代或递归方式完成反转。你能否用两种方法解决这道题？

#### 代码
``` python
# @lc code=start
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        next = ListNode()
        last = None 
        cur = head
        while(cur):
            next = cur.next
            cur.next= last
            last = cur
            cur = next
        return last
```
- 只需要改变链表的next指针的指向，直接将链表反转 ，而不用重新定义一个新的链表。但是要捋明白这个链表的前前后后，不然晕。