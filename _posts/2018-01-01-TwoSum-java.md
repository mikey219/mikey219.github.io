---
layout: post
title:  "TwoSum"
date:   2018-01-01 15:14:54
categories: leetcode
tags: leetcode algorithm java
excerpt: 
mathjax: true
---

## 1.Description
Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

Example:
>Given nums = [2, 7, 11, 15], target = 9,
>Because nums[0] + nums[1] = 2 + 7 = 9,return [0, 1].





## 2.Sulution
因为题目中没有涉及说是有序数组，所以想到的就是循环遍历，看是否满足题设返回即可。
	
```	
	public int[] twoSum(int[] nums, int target) {
        if (nums.length < 1) {
            return new int[]{};
        }
        int[] result = new int[2];	//a
        for (int i = 0; i < nums.length - 1; i++) {
            for (int j = i + 1; j < nums.length; j++) {
                if (nums[i] + nums[j] == target) {
                    result[0] = i;	//b
                    result[1] = j;
                }
            }
        }
        return result;
    }
```
   
第一遍写的程序跑测试用例的时候抛出了数组越界异常，检查后发现时数组初始化方法有问题。a处声明的是动态数组**却没有声明长度**，于是在b处赋值的时候异常。修改后通过测试用例。时间复杂度O(n^2)

## 3.Java数组初始化
### 3.1 静态初始化
	String cats[] = new String[] {"Tom","Sam","Mimi"};    
 	String dogs[] = {"Jimmy","Gougou","Doggy"}  

### 3.2 动态初始化
	String books[] = new String[2];  
	books[0] = "Thinking in Java";  
	books[1] = "Effective Java";  
    
## 4.其他
普通解法时间复杂度为O(n^2),空间复杂度为O(1)。如果想要降低时间复杂度，考虑用空间换时间，先用一个hashtable存储这个数组，然后遍历一遍获取满足条件的数对。这样时间复杂度是O(n),空间复杂度也为O(n).  
  
参考[TwoSum-Solution](https://leetcode.com/problems/two-sum/solution/)




    
