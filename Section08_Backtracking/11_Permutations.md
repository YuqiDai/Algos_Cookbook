# Permutations
## Link
[Permutations](https://leetcode.com/problems/permutations/description/)

## Code
```cpp
class Solution {
private:
    vector<int> permu;
    vector<vector<int>> ans;
    unordered_set<int> used;

    void backtrack(vector<int>& nums){
        if(permu.size()==nums.size()){
            ans.push_back(permu);
            return ;
        }

        for(int i=0;i<nums.size();i++){
            if(used.find(nums[i])!=used.end()){
                continue;
            }

            used.insert(nums[i]);
            permu.push_back(nums[i]);
            backtrack(nums);
            permu.pop_back();
            used.erase(nums[i]);
        }
    }
public:
    vector<vector<int>> permute(vector<int>& nums) {
        backtrack(nums);
        return ans;
    }
};
```

## Evaluation
![Permutations](./11.PNG)