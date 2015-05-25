---
layout: post
title:  "First Missing Positive"
date:   2015-04-02 12:00:12
categories: leetcode
---
[First Missing Positive](https://leetcode.com/problems/first-missing-positive/)  
Given an unsorted integer array, find the first missing positive integer.  

For example,  
Given [1,2,0] return 3,  
and [3,4,-1,1] return 2.  
  
Your algorithm should run in O(n) time and uses constant space.  

{% highlight c++ %}
class Solution {
public:
    int firstMissingPositive(int A[], int n) {
        int tempIdx = 0;
        int temp = 0;
        
        for (int idx = 0; idx < n; ++idx) {
            if (A[idx] > 0) {
                if (A[idx] > n) {
                    A[idx] = -1;
                } else if (A[idx] != idx + 1) {
                    tempIdx = A[idx];
                    A[idx] = -1;
                    
                    while (true) {
                        if (A[tempIdx - 1] == tempIdx || A[tempIdx - 1] < 1) {
                            A[tempIdx - 1] = tempIdx;
                            break;
                        } else {
                            temp = A[tempIdx - 1];
                            A[tempIdx - 1] = tempIdx;
                            tempIdx = temp;
                        }
                    }
                }
            }
        }
        
        for (int idx = 0; idx < n; ++idx) {
            if (A[idx] < 1) 
                return idx + 1;
        }
        
        return n + 1;
    }
};
{% endhighlight %}