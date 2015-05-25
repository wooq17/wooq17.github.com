---
layout: post
title:  "Pascal's Triangle"
date:   2015-05-16 12:00:12
categories: leetcode
---
[Pascal's Triangle](https://leetcode.com/problems/pascals-triangle/)  
Given numRows, generate the first numRows of Pascal's triangle.  
  
For example, given numRows = 5,  
Return  
{% highlight python %}
[
     [1],
    [1,1],
   [1,2,1],
  [1,3,3,1],
 [1,4,6,4,1]
]
{% endhighlight %}


{% highlight python %}
class Solution:
    # @param {integer} numRows
    # @return {integer[][]}
    def generate(self, numRows):
        if numRows == 0 : return []
        
        triangle = []
        triangle.append([1])
        
        for length in range(2, numRows+1) :
            current_row = []
            
            for idx in range(length) :
                left = triangle[length-2][idx-1] if idx != 0 else 0
                right = triangle[length-2][idx] if idx != length-1 else 0
                current_row.append(left + right)  
                
            triangle.append(current_row)
            
        return triangle
{% endhighlight %}