# 4 Sum
## Puzzle Description
Given an array ***nums*** of ***n*** integers, return *an array of all the ***unique*** quadruplets* $[nums[a], nums[b], nums[c], nums[d]]$ such that:

* $0 <= a, b, c, d < n$
* $a, b, c, and d are distinct.$
* $nums[a] + nums[b] + nums[c] + nums[d] == target$   

You may return the answer in any order.

## Methodology
1. Remember using ***long long int*** when assigning the ***sum*** of 4 elements.
2. Remember cutting branches.
3. The methodology else is the same as ***3 Sum***.

## Code
```cpp
class Solution {
public:
    std::vector<std::vector<int>> fourSum(std::vector<int>& nums, int target) {
        std::vector<std::vector<int>> ans;
        if(nums.size()<4){
            return ans;
        }
        std::sort(nums.begin(),nums.end());

        for(int i=0;i<nums.size()-3;i++){
            while(i>0&&nums[i-1]==nums[i]){
                i++;
            }
            for(int j=i+1;j<nums.size()-2;j++){
                while(j<nums.size()-2&&j>i+1&&nums[j-1]==nums[j]){
                    j++;
                }

                int left=j+1,right=nums.size()-1;
                while(left<right){
                    long long int sum=0;
                    sum+=nums[i];
                    sum+=nums[j];
                    sum+=nums[left];
                    sum+=nums[right];
                    if(sum==target){
                        std::vector<int> unit;
                        unit.push_back(nums[i]);
                        unit.push_back(nums[j]);
                        unit.push_back(nums[left]);
                        unit.push_back(nums[right]);
                        ans.push_back(unit);

                        while(left<right&&nums[left+1]==nums[left]){
                            left++;
                        }
                        left++;
                        while(left<right&&nums[right-1]==nums[right]){
                            right--;
                        }
                        right--;
                    }
                    else if(sum<target){
                        left++;
                    }
                    else{
                        right--;
                    }
                }
            }
        }

        return ans;
    }
};
```

## Evaluation
![img](./4%20Sum.png)