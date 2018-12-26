---
layout: post
title:  "TwoSum"
date:   2018-01-06 12:14:54
categories: leetcode
tags: leetcode algorithm java
excerpt: 
mathjax: true
---

## 1.Description
You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8





## 2.Solution
一开始边界条件没想清楚，没确定什么时候能够结束循环（什么时候进位生成新的节点）
	
	public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode listNode = new ListNode(0);
        ListNode result = listNode;
        int carry = 0;
        while (l1 != null || l2 != null) {
            boolean flag = false; //标识是否应该退出循环
            int val = l1.val + l2.val + carry;
            carry = val >= 10 ? 1 : 0;
            listNode.val = val % 10;
            if (l1.next != null || l2.next != null || carry == 1) {
                flag = true;
                listNode.next = new ListNode(0);
                listNode = listNode.next;
            }
            if (l1.next != null) {
                flag = true;
                l1 = l1.next;
            } else {
                l1.val = 0;
            }
            if (l2.next != null) {
                flag = true;
                l2 = l2.next;
            } else {
                l2.val = 0;
            }
            if (!flag) {
                break;
            }
        }
        return result;
    }

## 3.其他
时间复杂度：O（max(m,n)） m&n代表l1&l2的长度  
空间复杂度：O（max(m,n)） 新列表最长为max(m,n)+1  
参考答案：
	
	public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
    	ListNode dummyHead = new ListNode(0);
    	ListNode p = l1, q = l2, curr = dummyHead;
    	int carry = 0;
    	while (p != null || q != null) {
        	int x = (p != null) ? p.val : 0;
        	int y = (q != null) ? q.val : 0;
        	int sum = carry + x + y;
        	carry = sum / 10;
        	curr.next = new ListNode(sum % 10);
        	curr = curr.next;
        	if (p != null) p = p.next;
        	if (q != null) q = q.next;
    	}
    	if (carry > 0) {
        	curr.next = new ListNode(carry);
    	}
    	return dummyHead.next;
    }
