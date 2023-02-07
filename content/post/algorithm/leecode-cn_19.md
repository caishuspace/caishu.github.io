---
title: "19.删除链表的倒数第N个节点 "
description: "leecode-cn_19,删除链表的倒数第N个节点"
keywords: "leecode,cn_19,删除链表的倒数第N个节点"

date: 2023-01-07T23:01:42+08:00
lastmod: 2023-01-07T23:01:42+08:00

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
link: https://leetcode.cn/problems/remove-nth-node-from-end-of-list/
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
#url: "leecode-cn_19.html"
# 开启文章置顶，数字越小越靠前
# Sticky post set-top in home page and the smaller nubmer will more forward.
#weight: 1
---

删除链表的倒数第N个节点-使用双节点解题

<!--more-->
#### 题目描述
给你一个链表，删除链表的倒数第 n 个结点，并且返回链表的头结点。
    - 示例1 ：
```
输入：head = [1,2,3,4,5], n = 2
输出：[1,2,3,5]
```
- 示例2：
```
输入：head = [1], n = 1
输出：[]
```
- 示例3：
```
输入：head = [1,2], n = 1
输出：[1]
```
- 提示：
```
链表中结点的数目为 sz
1 <= sz <= 30
0 <= Node.val <= 100
1 <= n <= sz
```
#### 代码
 - 普通思路代码
 ``` python
 # @lc code=start
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def removeNthFromEnd(self, head: Optional[ListNode], n: int) -> Optional[ListNode]:
        h1 = ListNode(next=head)
        cur = h1.next
        cnt = 0
        tail = None

        while cur!= None:
            cur = cur.next
            cnt +=1
        
        k = cnt - n
        
        tmp = h1
        for i in range(0,k):
            tmp = tmp.next
        
        if tmp.next != None:
            tmp.next = tmp.next.next

        return h1.next
 ```

 - 进阶【使用一遍遍历解决，双指针方法】
 ```python
# @lc code=start
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def removeNthFromEnd(self, head: Optional[ListNode], n: int) -> Optional[ListNode]:
        h1 = ListNode(next=head)
        q = h1
        s = h1
        hh = h1.next
        for i in range(0,n):
            q=q.next

        while q.next != None :
            s = s.next
            q = q.next

        s.next = s.next.next

        return h1.next
 ```