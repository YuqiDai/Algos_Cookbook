# Maximum Subarray
## Link
[Maximum Subarray](https://leetcode.com/problems/maximum-subarray/description/)

## Code
```cpp
class Solution {
private:
    long long int gen_sum = 0;
    long long int repo_sum = 0;
public:
    int maxSubArray(vector<int>& nums) {
        gen_sum=nums[0];
        
        for(int i=0;i<nums.size();++i){
            repo_sum+=nums[i];
            if(repo_sum>gen_sum){
                gen_sum=repo_sum;
            }

            if(repo_sum<0){
                repo_sum=0;
                continue;
            }
        }

        return gen_sum;
    }
};
```

## Evaluation
![Maximum Subarray](./03.png)