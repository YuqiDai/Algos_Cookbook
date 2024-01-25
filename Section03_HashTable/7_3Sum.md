# 3Sum
## Puzzle Description
Given an integer array nums, return all the triplets **[nums[i], nums[j], nums[k]]** such that **i != j, i != k, and j != k**, and **nums[i] + nums[j] + nums[k] == 0**.   
   
Notice that the solution set must not contain duplicate triplets.

## Methodology
A skill must be remembered ***"Sort the unordered array first could help a lot in boundary conditions processing."***   

The puzzle solving process includes two parts. Part one: Finding all nums[x],nums[y],nums[z] which fullfill equation $nums[x]+nums[y]+nums[z]=0$. Second part is delete duplicated triple set. The tough part of this solution is on the second part. We need to handle it according to the skill above.   
   
First, we sort the vector; Then, we define 3 iterator which are i, left, right. i is the base iterator, left and right can be seen as the two pointers in twopointers mindset. We use i to make sure that we can traverse all the elements in this vector. To avoid duplication of nums[i], we use condition equation $nums[i]!=nums[i-1]$ to filter all repeated elements.   
      
After make the base iterator still, we assign $left=i+1$ and $right=nums.size()-1$. Then increase left by 1 each steps when $nums[x]+nums[y]+nums[z]<0$ or decrease right by 1 each steps when $nums[x]+nums[y]+nums[z]>0$. After finding the [i,left,right] triple set fullfills conditions, we need to handle the possibly occured ***left+1*** and ***right-1*** which makes $nums[left]==nums[left+1]$ and $nums[right]==nums[right-1]$ true.

Refer to code section for detail.

## Code
```cpp
class Solution {
public:
    std::vector<std::vector<int>> threeSum(std::vector<int>& nums) {
        int len=nums.size();
        std::sort(nums.begin(),nums.end());
        std::vector<std::vector<int>> ans;

        for(int i=0;i<len;i++){
            if(i!=0&&nums[i]==nums[i-1]){
                continue;
            }
            int left=i+1, right=len-1;
            while(left<right){
                if(nums[i]+nums[left]+nums[right]==0){
                    ans.push_back(std::vector<int>{nums[i],nums[left],nums[right]});

                    while(left<right&&nums[left]==nums[left+1]){left++;}
                    while(left<right&&nums[right]==nums[right-1]){right--;}
                    left++;
                    right--;
                }
                else if(nums[i]+nums[left]+nums[right]<0){
                    left++;
                }
                else{
                    right--;
                }
            }
        }

        return ans;
    }
};

```

## Evaluation
![img](./7_3Sum.png)