---
title: fenceoffer26
date: 2019-04-04 20:37:31
categories: 笔试
tags:
  - python
  - 剑指offer
  - 链表
---

## 复杂链表的复制
### 题目描述
输入一个复杂链表（每个节点中有节点值，以及两个指针，一个指向下一个节点，另一个特殊指针指向任意一个节点），返回结果为复制后复杂链表的head。（注意，输出结果中请不要返回参数中的节点引用，否则判题程序会直接返回空）
### 思路
1. 对每一个复制节点遍历找random，时间o(n^2)
2. 使用哈希记录节点，空间o(n)，时间o(n)
3. 将每一个节点复制一遍连接其后，如12345->1122334455。再将random复制为元random的next，最后将链表间隔拆开成两条。

    	# -*- coding:utf-8 -*-
		# class RandomListNode:
		#     def __init__(self, x):
		#         self.label = x
		#         self.next = None
		#         self.random = None

		class Solution:
		    # 返回 RandomListNode
		    def Clone(self, pHead):
		        # write code here
		        p = pHead
		        while p != None:
		            pclone = RandomListNode(p.label)
		            pclone.next = p.next
		            p.next = pclone
		            p = pclone.next
		        p = pHead
		        while p != None:
		            pclone = p.next
		            if p.random != None:
		                pclone.random = p.random.next
		            p = pclone.next
		        p = pHead
		        res = None
		        pclone = None
		        if p != None:
		            res = p.next
		            pclone = p.next
		            p.next = pclone.next
		            p = p.next
		        while p!=None:
		            pclone.next = p.next
		            pclone = pclone.next
		            p.next = pclone.next
		            p = p.next
		        return res