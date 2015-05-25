---
layout: post
title:  "Find Peak Element"
date:   2015-05-07 12:00:12
categories: leetcode
---
[Find Peak Element](https://leetcode.com/problems/find-peak-element/)  
A peak element is an element that is greater than its neighbors.  
Given an input array where num[i] ≠ num[i+1], find a peak element and return its index.  
The array may contain multiple peaks, in that case return the index to any one of the peaks is fine.  
You may imagine that num[-1] = num[n] = -∞.  
  
For example, in array [1, 2, 3, 1], 3 is a peak element and your function should return the index number 2.   

{% highlight python %}
class Solution:
    # @param nums, an integer[]
    # @return an integer
    def findPeakElement(self, nums):
        elementCount = len(nums)
        
        startIdx = 0
        endIdx = elementCount - 1
        mid = endIdx / 2
        
        while startIdx < endIdx :
            if (mid == startIdx or nums[mid-1] < nums[mid]) and (mid == endIdx or nums[mid] > nums[mid+1]) :
                break
            else :
                if mid > startIdx and nums[mid-1] > nums[mid] :
                    endIdx = mid - 1
                elif mid < endIdx and nums[mid] < nums[mid+1] :
                    startIdx = mid + 1
                    
            mid = endIdx + (startIdx - endIdx) / 2
            
        return mid 
{% endhighlight %}