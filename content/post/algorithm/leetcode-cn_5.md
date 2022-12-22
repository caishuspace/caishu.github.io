---
title: "最长回文子串"
description: "力扣刷题-最长回文子串-【中点扩散法】"
keywords: "leetcode,算法"

date: 2022-12-22T19:50:21+08:00
lastmod: 2022-12-22T19:50:21+08:00

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
link: https://leetcode.cn/problems/longest-palindromic-substring/description/
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

力扣刷题-最长回文子串
<!--more-->
#### 问题描述
给你一个字符串 s，找到 s 中最长的回文子串。

如果字符串的反序与原始字符串相同，则该字符串称为回文字符串。

- 示例1
``` text
输入：s = "babad"
输出："bab"
解释："aba" 同样是符合题意的答案。
```
- 示例1
``` text
输入：s = "cbbd"
输出："bb"
```
#### 提示：
- 1 <= s.length <= 1000
- s 仅由数字和英文字母组成

#### 代码
- 由于回文串是对称的，所以我们可以枚举所有的中点，再向两侧扩散，时间复杂度为O（n^2）。
``` python
# @lc code=start
class Solution:
    def longestPalindrome(self, s: str) -> str:
# @lc code=end
        len1 = len(s)
        maxlen= 0
        maxstr = ""
        for i in range(0,len1):
            left = i - 1
            right = i + 1
            while left>0 and right<len1 and s[left]==s[right]:
                left-=1
                right+=1
                if maxlen < (right-left-1):
                    maxlen = (right-left-1)
                    maxstr = s[left:right]
            left = i 
            right= i+1
            while left>0 and right<len1 and s[left]==s[right]:
                left-=1
                right+=1
                if maxlen < (right-left-1):
                    maxlen = (right-left-1)
                    maxstr = s[left:right]
        return maxstr              

```

## 