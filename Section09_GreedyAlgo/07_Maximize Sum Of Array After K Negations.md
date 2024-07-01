# Maximize Sum Of Array After K Negations
## Link
[Maximize Sum Of Array After K Negations](https://leetcode.com/problems/maximize-sum-of-array-after-k-negations/description/)

## Code
```cpp
class Solution {
public:
    int largestSumAfterKNegations(vector<int>& nums, int k) {
        sort(nums.begin(), nums.end());
        int t=k;
        int i=0;

        while(t>0){
            if(t<=0||i>=nums.size()) break;
            if(nums[i]<0){
                nums[i]=-nums[i];
                --t;
                ++i;
                continue;
            }

            break;
        }

        if(t%2!=0){
            sort(nums.begin(), nums.end());
            nums[0]=-nums[0];
        }
    
        int sum=0;
        for(int i=0;i<nums.size();++i){
            sum+=nums[i];
        }

        return sum;
    }
};
```

## Evaluation
![Maximize Sum Of Array After K Negations](./07.PNG)