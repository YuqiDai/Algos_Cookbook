# Combination Sum
## Link
[Combination Sum](https://leetcode.com/problems/combination-sum/)

## Code
```cpp
class Solution {
public:
    int sum=0;
    vector<int> unit;
    vector<vector<int>> ans;

    vector<vector<int>> combinationSum(vector<int>& candidates, int target) {
        backtrack(candidates, 0, target);

        return ans;
    }

    void backtrack(vector<int>& candidates, int index, int target){
        if(sum>target){
            return;
        }
        if(sum==target){
            ans.push_back(unit);
            return;
        }

        for(int i=index;i<candidates.size();i++){
            sum+=candidates[i];
            unit.push_back(candidates[i]);
            backtrack(candidates, i, target);
            sum-=candidates[i];
            unit.pop_back();
        }
    }
};
```

## Evaluation
![Combination Sum](./04.PNG)