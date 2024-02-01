# 3 Sum
## Notice
This puzzle has occured in ***Section 3***. And we will use the same methodology to handle it. So if you are familiar with it, you can go throught the next puzzle instead of doing this one again.
## Puzzle Description
Given an integer array nums, return all the triplets **[nums[i], nums[j], nums[k]]** such that **i != j, i != k, and j != k**, and **nums[i] + nums[j] + nums[k] == 0**.   
   
Notice that the solution set must not contain duplicate triplets.

## Methodology
Main ideas in this puzzle:
1. Way to traverse an array
2. Branches cutting

For the first point, we sort the array then using multiple loops to traverse. The time complexity there is high but no way to reduce it.   
For the second point, we cut the same elements in an array.

## Code 
```c++
class Solution {
public:
    std::vector<std::vector<int>> threeSum(std::vector<int>& nums) {
        std::vector<std::vector<int>> ans;
        std::sort(nums.begin(),nums.end());
        
        for(int i=0;i<nums.size()-2;i++){
            int left=i+1, right=nums.size()-1;
            while(left<right){
                if(nums[i]+nums[left]+nums[right]==0){
                    std::vector<int> unit;
                    unit.push_back(nums[i]);
                    unit.push_back(nums[left]);
                    unit.push_back(nums[right]);
                    ans.push_back(unit);
                    while(left<right&&nums[left+1]==nums[left]){
                        left++;
                    }
                    while(left<right&&nums[right-1]==nums[right]){
                        right--;
                    }
                }
                else if(nums[i]+nums[left]+nums[right]<0){
                    left++;
                }
                else{
                    right--;
                }
            }
            while(nums[i+1]==nums[i]&&i<nums.size()-2){
                i++;
            }
        }

        return ans;
    }
};
```

## Evaluation
![img](./3%20Sum.png)