---
layout: post
title:  "Insertion Sort List"
date:   2015-04-12 12:00:10
categories: leetcode
---
[Insertion Sort List](https://leetcode.com/problems/insertion-sort-list/)  
Sort a linked list using insertion sort.  

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
    ListNode *insertionSortList(ListNode *head) {
        ListNode* sentinel = new ListNode(0);
        ListNode* current = head;
        ListNode* next = nullptr;
        ListNode* prev = nullptr;
        
        while (current != nullptr) {
            next = current->next;
            prev = sentinel;
            
            while (prev->next != nullptr && prev->next->val <= current->val)
                prev = prev->next;
            
            current->next = prev->next;
            prev->next = current;
            current = next;
        }
        
        ListNode* ret = sentinel->next;
        delete sentinel;
        
        return ret;
    }
};
{% endhighlight %}