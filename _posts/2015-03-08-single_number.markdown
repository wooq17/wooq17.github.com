---
layout: post
title:  "Single Number"
date:   2015-06-08 12:00:10
categories: leetcode
---
[Single Number](https://leetcode.com/problems/single-number/)  
Given an array of integers, every element appears twice except for one. Find that single one.  

Note:  
Your algorithm should have a linear runtime complexity. Could you implement it without using extra memory?

{% highlight python %}
class Solution {
public:
    int singleNumber(int A[], int n) {
        int returnVal = 0;
        
        for (int i = 0; i < n; ++i)
            returnVal ^= A[i];
            
        return returnVal;
    }
};
{% endhighlight %}