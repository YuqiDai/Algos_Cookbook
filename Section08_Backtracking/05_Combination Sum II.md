# Combination Sum II
## Link
[Combination Sum II](https://leetcode.com/problems/combination-sum-ii/description/)

## Code
```cpp
class Solution {
private:
    vector<int> unit;
    vector<vector<int>> ans;
    int sum=0;
public:
    vector<vector<int>> combinationSum2(vector<int>& candidates, int target) {
        sort(candidates.begin(), candidates.end());
        backtrack(candidates, target, 0);
        return ans;
    }

    void backtrack(vector<int>& candidates, int target, int index){
        if(sum>target) return;
        else if(sum==target){ans.push_back(unit); return ;}

        for(int i=index;i<candidates.size();i++){
            if(i>index && candidates[i]==candidates[i-1]) continue;
            sum+=candidates[i];
            unit.push_back(candidates[i]);
            backtrack(candidates, target, i+1);
            unit.pop_back();
            sum-=candidates[i];
        }
    }
};
```

## Evaluation
![Combination Sum II](./05.PNG)