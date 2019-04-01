---
title: 排序二叉树删除节点
date: 2019-04-01 18:46:38
categories:	刷题
tags:
  - leetcode
  - BST 
---

	# Definition for a binary tree node.
	# class TreeNode(object):
	#     def __init__(self, x):
	#         self.val = x
	#         self.left = None
	#         self.right = None
	
	class Solution(object):
	    def deleteNode(self, root, key):
	        """
	        :type root: TreeNode
	        :type key: int
	        :rtype: TreeNode
	        """
	        p = root
	        pre = None
	        while p:
	            if p.val == key:
	                break
	            elif p.val > key:
	                pre = p
	                p = p.left
	            else:
	                pre = p
	                p = p.right
	        if p == None:
	            return root
	        elif p.left==None and p.right==None:
	            if pre == None:
	                root = None
	            elif pre.val > key:
	                pre.left = None
	            else:
	                pre.right = None
	        elif p.left!=None and p.right==None:
	            if pre == None:
	                root = p.left
	            elif pre.val > key:
	                pre.left = p.left
	            else:
	                pre.right = p.left
	        elif p.left==None and p.right!=None:
	            if pre == None:
	                root = p.right
	            elif pre.val > key:
	                pre.left = p.right
	            else:
	                pre.right = p.right
	        else:
	            rep = p.left
	            repp = p
	            while rep.right:
	                repp = rep
	                rep = rep.right
	            if repp.val > rep.val:
	                repp.left = rep.left
	            else:
	                repp.right = rep.left
	            p.val = rep.val
	        return root
                
                
                
        