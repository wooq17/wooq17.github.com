---
layout: post
title:  "Maximal Rectangle"
date:   2015-04-12 12:00:11
categories: leetcode
---
[Maximal Rectangle](https://leetcode.com/problems/maximal-rectangle/)  
Given a 2D binary matrix filled with 0's and 1's, find the largest rectangle containing all ones and return its area.  

{% highlight c++ %}
class Solution {
public:
    int maximalRectangle(vector<vector<char>> &matrix) {
        matrixSizeY = matrix.size();
        if (matrixSizeY == 0) {
            return 0;
        }
        matrixSizeX = matrix[0].size();
        
        cache.resize(matrixSizeX * matrixSizeY);
        fill(cache.begin(), cache.end(), -1);
        
        return findMaximumArea(0, matrixSizeY - 1, matrix);
    }
    
    int findMaximumArea(int startY, int endY, const vector<vector<char>> &matrix) {
        if (startY > endY) {
            return 0;
        }
        
        int midY = startY + (endY - startY) / 2;
    
        int prevMaxArea = findMaximumArea(startY, midY - 1, matrix);
        int nextMaxArea = findMaximumArea(midY + 1, endY, matrix);
        int maxArea = 0;
    
        for (int idxX = 0; idxX < matrixSizeX; ++idxX) {
            int tempHeight = findHeight(idxX, midY, matrix);
    
            for (int localHieght = 1; localHieght <= tempHeight; ++localHieght) {
                int lenUpper = findExtensionLen(idxX, midY - 1, localHieght, -1, matrix);
                int lenLower = findExtensionLen(idxX, midY + 1, localHieght, 1, matrix);
    
                int tempArea = (lenLower + lenUpper + 1) * localHieght;
                maxArea = max(maxArea, tempArea);
            }
        }
    
        maxArea = max(maxArea, prevMaxArea);
        maxArea = max(maxArea, nextMaxArea);
    
        return maxArea;
    }

    int findHeight(int startPosX, int posY, const vector<vector<char>> &matrix) {
        int currentIdx = matrixSizeX * posY + startPosX;
        
        if (cache[currentIdx] != -1) {
            return cache[currentIdx];
        }
        
        int result = 0;
        int currentX = startPosX;
    
        while (currentX < matrixSizeX && matrix[posY][currentX] == '1') {
            ++result;
            ++currentX;
        }
        
        for (int i = 0; i < result; ++i) {
            cache[matrixSizeX * posY + startPosX + i] = result - i;
        }
    
        return result;
    }

    int findExtensionLen(int posX, int startPosY, int height, int direction, const vector<vector<char>> &matrix) {
        int len = 0;
        int currentY = startPosY;
    
        while (currentY >= 0 && currentY < matrixSizeY && findHeight(posX, currentY, matrix) >= height) {
            ++len;
            currentY += direction;
        }
    
        return len;
    }
    
private:
    int matrixSizeX = 0;
    int matrixSizeY = 0;
    
    vector<int> cache;
};
{% endhighlight %}