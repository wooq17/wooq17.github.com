---
layout: post
title:  "Max Points on a Line"
date:   2015-04-29 12:00:11
categories: leetcode
---
[Max Points on a Line](https://leetcode.com/problems/max-points-on-a-line/)  
Given n points on a 2D plane, find the maximum number of points that lie on the same straight line.  

{% highlight c++ %}
/**
 * Definition for a point.
 * struct Point {
 *     int x;
 *     int y;
 *     Point() : x(0), y(0) {}
 *     Point(int a, int b) : x(a), y(b) {}
 * };
 */
class Solution {
public:
    int maxPoints(vector<Point> &points) {
        int returnVal = 0;

        unsigned int pointsCount = points.size();
        std::map<float, unsigned int> lineCount;

        for (unsigned int i = 0; i < pointsCount; ++i) {
            unsigned int duplicated = 0;
            unsigned int verticallyAligned = 1;
            unsigned int maxCount = 1;
            lineCount.clear();
    
            for (unsigned int j = i + 1; j < pointsCount; ++j) {
                float gradient = 0.0f;
                int dx = points[j].x - points[i].x;
                
                if (dx == 0) {
                    if (points[j].y == points[i].y) {
                        ++duplicated;
                    } else {
                        ++verticallyAligned;
                    }
                } else {
                    gradient = static_cast<float>( points[j].y - points[i].y ) / dx;

                    std::map<float, unsigned int>::iterator iter = lineCount.find( gradient );
                    if (iter == lineCount.end()) {
                        lineCount.insert(std::map<float, unsigned int>::value_type(gradient, 2));
                    } else {
                        ++lineCount[gradient];
                    }
                    
                    maxCount = (maxCount > lineCount[gradient]) ? maxCount : lineCount[gradient];
                }
            }
            
            maxCount = ( maxCount > verticallyAligned ) ? maxCount : verticallyAligned;
            maxCount += duplicated;
            
            returnVal = ( returnVal > maxCount ) ? returnVal : maxCount;
        }
    
        return returnVal;
    }
};          
{% endhighlight %}