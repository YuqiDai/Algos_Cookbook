# Array_remove elements
## Puzzle Description
Given an integer array ***nums*** and an integer ***val***, remove all occurrences of ***val*** in ***nums*** in-place. The order of the elements may be changed. Then return the number of elements in ***nums*** which are not equal to ***val***.   
Refer to Leetcode link [Remove Element](https://leetcode.com/problems/remove-element/description/)

Consider the number of elements in ***nums*** which are not equal to ***val*** be ***k***, to get accepted, you need to do the following things:

* Change the array ***nums*** such that the first ***k*** elements of ***nums*** contain the elements which are not equal to ***val***. The remaining elements of ***nums*** are not important as well as the size of ***nums***.
* Return ***k***.

## Methodology
This puzzle occured in ***Section1_Array*** before, I thought I can handle it within a few mins but actually I spent nearly an hour to fix it up again. So, the main problem here is that I'm still not familiar with how to process boundaries questions in array. That's why I choose to exhibit this puzzle again.

## Code
```c++
class Solution {
public:
    int removeElement(std::vector<int>& nums, int val) {
        int i=0,j=nums.size()-1;
        for(;i<=j;i++){
            if(nums[i]==val){
                std::swap(nums[i--],nums[j--]);
            }
        }

        return j+1;
    }
};
```

## Evaluation
![img](Array_remove%20elements.png)