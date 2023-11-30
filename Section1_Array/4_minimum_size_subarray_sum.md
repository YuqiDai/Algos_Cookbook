# Minimum Size Subarray Sum
## Puzzle Description
Given an array of positive integers ***nums*** and a positive integer ***target***, return the minimal length of a subarray whose sum is greater than or equal to ***target***. If there is no such subarray, return ***0*** instead.

## Methodology
Using two pointers method (There is specifically sliding window method) to traverse the array. Two pointers method could cut redundent branches which would enhance the efficiency of this algorithm obviously.   

## Code
```c++
class Solution {
public:
    int minSubArrayLen(int target, vector<int>& nums) {

        int len=nums.size();
        long long int sum=0;

        int sublen=INT_MAX;
        int begin=0,end=0;

        while(end<len){
            sum+=nums[end];
            while(sum>=target){
                if(sublen>(end-begin+1)){
                    sublen=end-begin+1;
                }
                sum-=nums[begin];
                ++begin;
            }
            ++end;
        }

        return sublen==INT_MAX?0:sublen;
    }
};
```
## Evaluation
![img](./4_minimum_size_subarray_sum.png)
