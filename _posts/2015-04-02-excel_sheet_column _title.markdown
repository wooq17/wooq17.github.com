---
layout: post
title:  "Excel Sheet Column Title"
date:   2015-04-02 12:00:11
categories: leetcode
---
[Excel Sheet Column Title](https://leetcode.com/problems/excel-sheet-column-title/)  
Given a positive integer, return its corresponding column title as appear in an Excel sheet.  
  
For example:  
    1 -> A  
    2 -> B  
    3 -> C  
    ...  
    26 -> Z  
    27 -> AA  
    28 -> AB  

{% highlight python %}
class Solution:
    # @return a string
    def convertToTitle(self, num):
        resultNumbers = []
        baseChar = ord('A')

        returnValue = ''
        srcNumber = num

        while True :
            srcNumber = srcNumber - 1
            returnValue = chr(srcNumber % 26 + baseChar) + returnValue
            srcNumber = srcNumber / 26
            
            if srcNumber is 0 :
                break

        return returnValue
{% endhighlight %}