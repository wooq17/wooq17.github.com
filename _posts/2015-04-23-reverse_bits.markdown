---
layout: post
title:  "Reverse Bits"
date:   2015-04-23 12:00:11
categories: leetcode
---
[Reverse Bits](https://leetcode.com/problems/reverse-bits/)  
Reverse bits of a given 32 bits unsigned integer.  
  
For example, given input 43261596 (represented in binary as 00000010100101000001111010011100), return 964176192 (represented in binary as 00111001011110000010100101000000).  
  
Follow up:  
If this function is called many times, how would you optimize it?  

{% highlight c++ %}
uint32_t reverseBits(uint32_t n) {
    uint32_t m;

    m = (n ^ (n >> 1) ) & 0x55555555;
    n = ((n & 0x55555555) ^ m) | ((n & (0x55555555 << 1)) ^ (m << 1));

    m = (n ^ (n >> 2) ) & 0x33333333;
    n = ((n & 0x33333333) ^ m) | ((n & (0x33333333 << 2)) ^ (m << 2));

    m = (n ^ (n >> 4) ) & 0x0F0F0F0F;
    n = ((n & 0x0F0F0F0F) ^ m) | ((n & (0x0F0F0F0F << 4)) ^ (m << 4));

    m = (n ^ (n >> 8) ) & 0x00FF00FF;
    n = ((n & 0x00FF00FF) ^ m) | ((n & (0x00FF00FF << 8)) ^ (m << 8));

    m = (n ^ (n >> 16) ) & 0x0000FFFF;
    n = ((n & 0x0000FFFF) ^ m) | ((n & (0x0000FFFF << 16)) ^ (m << 16));
    
    return n;
}
{% endhighlight %}