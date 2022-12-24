---
title: "Leetcode Cn_5"
description: "leetcode-cn_5"
keywords: "leetcode,cn_5"

date: 2022-12-24T19:52:48+08:00
lastmod: 2022-12-24T19:52:48+08:00

categories:
  - 算法刷题
tags:
  - 力扣刷题
  - 字符串
# categories:技术积累、论文阅读、问题解决、算法刷题、其他等四个条目，其余放在tags里面。

# 原文作者
# Post's origin author name
#author:
# 原文链接
# Post's origin link URL
link: https://leetcode.cn/problems/longest-substring-without-repeating-characters/
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
#url: "leetcode-cn_5.html"
# 开启文章置顶，数字越小越靠前
# Sticky post set-top in home page and the smaller nubmer will more forward.
#weight: 1
---

力扣刷题-无重复字符的最长子串

<!--more-->

#### 问题描述
 给定一个字符串 s ，请你找出其中不含有重复字符的 最长子串 的长度。
- 示例 1:
``` text
输入: s = "abcabcbb"
输出: 3 
解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。
```
- 示例 2:
``` text
输入: s = "bbbbb"
输出: 1
解释: 因为无重复字符的最长子串是 "b"，所以其长度为 1。
```
- 示例 3:
``` text
输入: s = "pwwkew"
输出: 3
解释: 因为无重复字符的最长子串是 "wke"，所以其长度为 3。
     请注意，你的答案必须是 子串 的长度，"pwke" 是一个子序列，不是子串。
```
- 提示：
``` text
0 <= s.length <= 5 * 104
s 由英文字母、数字、符号和空格组成
```

#### 代码
- 解题思路：使用滑动窗口解题。
算法思想：类似之前的思路，使用 window 作为计数器记录窗口中的字符出现次数，然后先向右遍历字符串s，当 window 中出现重复字符时，开始移动 left 缩小窗口，如此往复。显然还是O(N)。
移动的细节边界处理：依次向右寻找字符出现次数，遍历字符串s,用一个字典或者map或者set 存储出现的字符。我们这里选择使用字典，记录重复出现字符的下标位置。若字母未出现过，或者出现过但是当下时刻未在滑动窗口之内(即字典对应的字符串的值dic[s[i]]，小于left)，则计算长度。否则，窗口左侧移动到当前字母上次出现的下一个，同时更新当下字母的字典值。

``` python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        length = len(s)
        maxlen = 0
        left = 0
        dic = {}
        for i in range(0,length):
            if s[i] not in dic.keys() or dic[s[i]] < left:
                maxlen = max(maxlen,i-left+1)
                dic[s[i]]=i  
            else:
                left=dic[s[i]]+1
                dic[s[i]]=i 
        return maxlen

```