---
layout: post
title:  "PalindromeNumber"
date:   2018-01-19 15:14:54
categories: leetcode
tags: leetcode algorithm java
excerpt: 
mathjax: true
---

## 1.Description
Determine whether an integer is a palindrome. Do this without extra space.






## 2.Solution
首先需要注意的是：负数不是回文数。
其次需要注意，题设中不允许使用extra space，对这个extra space的理解，如果完全不使用任何额外空间，没想到什么解法，参考了一下答案，也定义了中间变量保存数据（参考答案的讨论区域对此争议很大，认为如果不是用extra space的话严格来说不能定义变量）。不考虑如此严格的话，给出了两个解法。一是将数字转成字符，进行字符比较；第二是将数字完全逆序，看新数是否与原数相等。  
解法一：

	public boolean isPalindrome(int x) {
        if (x < 0) {
            return false;
        }
        if (x < 10) {
            return true;
        }
        String temp = String.valueOf(x);
        for (int i = 0, j = temp.length() - 1; i <= j; i++, j--) {
            if (temp.charAt(i) != temp.charAt(j)) {
                return false;
            }
        }
        return true;
    }
    
解法二：

	public boolean isPalindrome(int x) {
        if (x < 0) {
            return false;
        }
        if (x < 10) {
            return true;
        }
        int temp = x;
        int result = 0;
        while (temp >= 10) {
            result = result * 10 + temp % 10;
            temp /= 10;
        }
        result = result * 10 + temp;
        return result == x;
    }
