# Permutations II
## Link
[Permutations II](https://leetcode.com/problems/permutations-ii/description/)

## Code
```cpp
class Solution {
private:
    vector<int> ele;
    vector<vector<int>> ans;

    void bt(vector<int>& nums){
        if(nums.size()==0){
            ans.push_back(ele);
            return ;
        }

        for(int i=0;i<nums.size();i++){
            if(i>0&&nums[i]==nums[i-1]){
                continue;
            }

            vector<int> tp=nums;
            tp.erase(tp.begin()+i);
            ele.push_back(nums[i]);
            bt(tp);
            ele.pop_back();
        }
    }

public:
    vector<vector<int>> permuteUnique(vector<int>& nums) {
        sort(nums.begin(), nums.end());
        bt(nums);
        return ans;
    }
};
```

## Evaluation
![Permutations II](./12.PNG)