# Find the Duplicate Number
## Link
[Find the Duplicate Number](https://leetcode.com/problems/find-the-duplicate-number/description/)

## Code
```cpp
class Solution {
public:
    int findDuplicate(vector<int>& nums) {
        sort(nums.begin(), nums.end());
        for(int i=0;i<nums.size();i++){
            if(i>0&&nums[i]==nums[i-1]) return nums[i];
        }

        return 0;
    }
};
```

## Evaluation
![Find the Duplicate Number](./01.PNG)