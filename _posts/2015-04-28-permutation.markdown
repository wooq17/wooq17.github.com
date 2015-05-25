---
layout: post
title:  "Permutations"
date:   2015-04-28 12:00:12
categories: leetcode
---
[Permutations](https://leetcode.com/problems/permutations/)  
Given a collection of numbers, return all possible permutations.  
  
For example,  
[1,2,3] have the following permutations:  
[1,2,3], [1,3,2], [2,1,3], [2,3,1], [3,1,2], and [3,2,1].  

{% highlight python %}
class Solution:
    # @param num, a list of integer
    # @return a list of lists of integers
    def permute(self, num):
        retVal = []
        
        self.recursion(num, 0, retVal);
            
        return retVal
        
        
    def recursion(self, num, idx, retVal):
        if idx == len(num) - 1 :
            temp = []
            for each in num :
                temp.append(each)
            retVal.append(temp)
            return
        
        for each in range(idx, len(num)) :
            self.swap(idx, each, num);
            self.recursion(num, idx + 1, retVal)
            self.swap(idx, each, num);
            
    def swap(self, idx1, idx2, num) :
        temp = num[idx2]
        num[idx2] = num[idx1]
        num[idx1] = temp
{% endhighlight %}