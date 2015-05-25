---
layout: post
title:  "Combinations"
date:   2015-03-06 12:00:00
categories: leetcode
---
[Combinations](https://leetcode.com/problems/combinations/)  
Given two integers n and k, return all possible combinations of k numbers out of 1 ... n.

{% highlight python %}
class Solution:
    def build(self, item, currentLen, start, end, targetLen, returnValue):
        if start > end :
            return

        for eachNum in range(start, end) :
            newItem = []
            for temp in item :
                newItem.append(temp)

            newItem.append(eachNum)
            len = currentLen + 1

            if targetLen - len <= 0 :
                returnValue.append(newItem)
            else :
                self.build(newItem, len, eachNum + 1, end, targetLen, returnValue)
                
    # @return a list of lists of integers
    def combine(self, n, k):
        returnVal = []
        currentItem = []
        self.build(currentItem, 0, 1, n + 1, k, returnVal)

        return returnVal    
{% endhighlight %}