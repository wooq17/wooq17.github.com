---
layout: post
title:  "Rotate List"
date:   2015-03-22 12:00:10
categories: leetcode
---
[Rotate List](https://leetcode.com/problems/rotate-list/)  
Given a list, rotate the list to the right by k places, where k is non-negative.  
  
For example:  
Given 1->2->3->4->5->NULL and k = 2,  
return 4->5->1->2->3->NULL.  

{% highlight c++ %}
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode *rotateRight(ListNode *head, int k) {
        if (head == nullptr || k == 0)
            return head;
            
        ListNode* curr = head;
        int listLen = 1;
        while (curr->next != nullptr) {
            ++listLen;
            curr = curr->next;
        }
        
        int rotateNum = k % listLen;
        if (rotateNum == 0)
            return head;
        
        int lastPos = listLen - rotateNum - 1;
        
        ListNode* lastNode = head;
        for (int i = 1; i <= lastPos; ++i) {
            lastNode = lastNode->next;
        }
    
        ListNode* startNode = lastNode->next;
        curr->next = head;
        lastNode->next = nullptr;
        
        return startNode;
    }
};
{% endhighlight %}