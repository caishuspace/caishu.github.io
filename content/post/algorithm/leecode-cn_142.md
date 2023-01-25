---
title: "142. 环形链表 II"
description: "leecode-cn_142"
keywords: "leecode,链表"

date: 2023-01-25T19:55:33+08:00
lastmod: 2023-01-25T19:55:33+08:00

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
link: https://leetcode.cn/problems/linked-list-cycle-ii/
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
#url: "leecode-cn_142.html"
# 开启文章置顶，数字越小越靠前
# Sticky post set-top in home page and the smaller nubmer will more forward.
#weight: 1
---

142. 环形链表 II - 使用快慢指针判断环的存在

两知识点：
- 判断链表是否环
- 如果有环，如何找到这个环的入口

<!--more-->
#### 题目描述
给定一个链表的头节点  head ，返回链表开始入环的第一个节点。 如果链表无环，则返回 null。

如果链表中有某个节点，可以通过连续跟踪 next 指针再次到达，则链表中存在环。 为了表示给定链表中的环，评测系统内部使用整数 pos 来表示链表尾连接到链表中的位置（索引从 0 开始）。如果 pos 是 -1，则在该链表中没有环。注意：pos 不作为参数进行传递，仅仅是为了标识链表的实际情况。

不允许修改 链表。

- 示例1 ：
![](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist.png "图片title")
```
输入：head = [3,2,0,-4], pos = 1
输出：返回索引为 1 的链表节点
解释：链表中有一个环，其尾部连接到第二个节点。 
```



- 提示：
```
链表中节点的数目范围在范围 [0, 104] 内
-105 <= Node.val <= 105
pos 的值为 -1 或者链表中的一个有效索引
```

#### 代码
###### 思路知识点
[原文参考](https://www.programmercarl.com/0142.%E7%8E%AF%E5%BD%A2%E9%93%BE%E8%A1%A8II.html#%E6%80%9D%E8%B7%AF "")。

- 判断链表是否有环

可以使用快慢指针法，分别定义 fast 和 slow 指针，从头结点出发，fast指针每次移动两个节点，slow指针每次移动一个节点，如果 fast 和 slow指针在途中相遇 ，说明这个链表有环。
为什么fast 走两个节点，slow走一个节点，有环的话，一定会在环内相遇呢，而不是永远的错开呢?
首先第一点：fast指针一定先进入环中，如果fast指针和slow指针相遇的话，一定是在环中相遇，这是毋庸置疑的。
那么来看一下，为什么fast指针和slow指针一定会相遇呢？
可以画一个环，然后让 fast指针在任意一个节点开始追赶slow指针。
会发现最终都是这种情况， 如下图：
![](https://img-blog.csdnimg.cn/20210318162236720.png "图片title")

fast和slow各自再走一步， fast和slow就相遇了
这是因为fast是走两步，slow是走一步，其实相对于slow来说，fast是一个节点一个节点的靠近slow的，所以fast一定可以和slow重合。
动画如下：
![](https://code-thinking.cdn.bcebos.com/gifs/141.%E7%8E%AF%E5%BD%A2%E9%93%BE%E8%A1%A8.gif "图片title")


- 如果有环，如何找到这个环的入口
从头结点出发一个指针，从相遇节点 也出发一个指针，这两个指针每次只走一个节点， 那么当这两个指针相遇的时候就是 环形入口的节点。

- python代码
``` python
# @lc code=start
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def detectCycle(self, head: Optional[ListNode]) -> Optional[ListNode]:
        h1 = ListNode(next = head)

        slow = head
        quick = head
        while quick != None and quick.next !=None:
            slow = slow.next
            quick = quick.next.next
            if slow ==quick:
                l1 = quick
                l2 = head
                while l1 != l2:
                    l1=l1.next
                    l2=l2.next
                return l2        

        return None
```