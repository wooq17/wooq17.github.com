---
layout: post
title:  "Reverse String"
date:   2015-03-14 12:00:10
categories: leetcode
---
[Reverse String](https://leetcode.com/problems/reverse-integer/)  
Reverse digits of an integer.  

Example1: x = 123, return 321  
Example2: x = -123, return -321  

{% highlight c++ %}
class Solution {
public:
    int reverse(int x) {
        long result = 0;
        int source = x;
        int sign = 1;
        
        if (x < 0) {
            sign = -1;
            source = ~x + 1;
        }
        
        while (source != 0) {
            result *= 10;
            result += source % 10;
            source /= 10;
        }
        
        result = sign * result;
        
        if (result > 2147483647 || result < -2147483648)
            return 0;
        
        return (int)result;
    }
};
{% endhighlight %}