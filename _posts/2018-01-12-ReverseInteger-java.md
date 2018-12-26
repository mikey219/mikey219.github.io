---
layout: post
title:  "ReverseInteger"
date:   2018-01-12 15:14:54
categories: leetcode
tags: leetcode algorithm java
excerpt: 
mathjax: true
---

## 1.Description
Given a 32-bit signed integer, reverse digits of an integer.  

**Example 1:**
> Input: 123  
> Output: 321

**Example 2:**
> Input: -123  
> Output: -321

**Example 3:**
> Input: 120  
> Output: 21

**Note:**
Assume we are dealing with an environment which could only hold integers within the 32-bit signed integer range. For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.








## 2.Solution
算法思路比较简单，要关注的就是边界条件。第一个问题就是，当输入为Integer.MIN_VALUE的时候，直接按照相反数去计算，int溢出了
> 32 位有符号int的值域是 -2^31 ~ 2^31-1  
> 即 -2147483648 到 2147483647  

所以对 x = -2147483648 程序做了单独处理。第二个问题是需要满足题设『溢出时返回0』的要求，于是采用 long 来做中间数据的存储并判断是否溢出。

	public int reverse(int x) {
        if (x == Integer.MIN_VALUE) {
            return 0;
        }
        if (x < 0) {
            return -1 * reverse(-1 * x);
        }
        long result = 0;
        long temp = (long) x;
        while (temp >= 10) {
            long tail = temp % 10;
            result = result * 10 + tail;
            temp /= 10;
        }
        result = result * 10 + temp;
        if (result > Integer.MAX_VALUE) {
            return 0;
        }
        return (int) result;
    }
