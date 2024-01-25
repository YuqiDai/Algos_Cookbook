# 4Sum
## Puzzle Description
Given an array ***nums*** of ***n*** integers, return *an array of all the ***unique*** quadruplets* $[nums[a], nums[b], nums[c], nums[d]]$ such that:

* $0 <= a, b, c, d < n$
* $a, b, c, and d are distinct.$
* $nums[a] + nums[b] + nums[c] + nums[d] == target$   

You may return the answer in any order.

## Methodology
Refer to 3Sum.

## Code
```cpp
class Solution {
public:
    std::vector<std::vector<int>> fourSum(std::vector<int>& nums, int target) {
        std::vector<std::vector<int>> ans;
        std::sort(nums.begin(),nums.end());
        int len=nums.size();

        for(int i=0;i<len;i++){
            if(target>=0&&nums[i]>target){return ans;}
            if(i!=0&&nums[i]==nums[i-1]){
                continue;
            }

            for(int j=i+1;j<len;j++){
                if(j-1!=i&&nums[j]==nums[j-1]){
                    continue;
                }
                int left=j+1,right=len-1;

                while(left<right){
                    long long int sum=nums[i];
                    sum+=nums[j];
                    sum+=nums[left];
                    sum+=nums[right];
                    if(sum<target){
                        left++;
                    }
                    else if(sum>target){
                        right--;
                    }
                    else{
                        ans.push_back(std::vector<int>{nums[i],nums[j],nums[left],nums[right]});

                        while(left<right&&nums[left]==nums[left+1]){left++;}
                        while(left<right&&nums[right]==nums[right-1]){right--;}

                        left++,right--;
                    }
                }

            }
        }

        return ans;
    }
};
```

## Evaluation
![img](./8_4Sum.png)