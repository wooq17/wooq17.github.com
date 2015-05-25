---
layout: post
title:  "Remove Nth Node From End of List"
date:   2015-05-05 12:00:11
categories: leetcode
---
[Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)  
Given a linked list, remove the nth node from the end of list and return its head.  
  
For example,  
   Given linked list: 1->2->3->4->5, and n = 2.  
   After removing the second node from the end, the linked list becomes 1->2->3->5.  
  
Note:  
Given n will always be valid.  
Try to do this in one pass.  

{% highlight python %}
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    # @param {ListNode} head
    # @param {integer} n
    # @return {ListNode}
    def removeNthFromEnd(self, head, n):
        sentinelNode = ListNode(0)
        sentinelNode.next = head
        
        endNode = sentinelNode
        targetNode = sentinelNode
        
        for each in range(n) :
            endNode = endNode.next
            
        while endNode.next != None :
            endNode = endNode.next
            targetNode = targetNode.next
            
        targetNode.next = targetNode.next.next
        
        return sentinelNode.next     
{% endhighlight %}