# Combinations
## Link
[Combinations](https://leetcode.com/problems/combinations/description/)

## Code
```cpp
class Solution {
private: 
    vector<vector<int>> ans;
    vector<int> unit;
public:
    vector<vector<int>> combine(int n, int k) {
        core(n, k, 1);
        return ans;
    }

    void core(int n, int k, int lf){
        if(unit.size()==k){
            ans.push_back(unit);
            return ;
        }

        for(int j=lf;j<=n;j++){
            unit.push_back(j);
            core(n, k, j+1);
            unit.pop_back();
        }
    }
};
```

## Evaluation
![Combinations](./01.png)