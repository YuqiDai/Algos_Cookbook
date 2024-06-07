# Combination Sum III
## Link
[Combination Sum III](https://leetcode.com/problems/combination-sum-iii/description/)

## Code
```cpp
class Solution {
private:
    vector<vector<int>> ans;
    vector<int> unit;
public:
    vector<vector<int>> combinationSum3(int k, int n) {
        if(n>45||n==1){
            return ans;
        }
        backtrack(k, n, 1);
        return ans;
    }

    void backtrack(int k, int n, int index){
        if(unit.size()==k){
            int sum=0;
            for(int i=0;i<unit.size();i++){
                sum+=unit[i];
            }
            if(sum==n){
                ans.push_back(unit);
            }

            return ;
        }

        for(int i=index;i<10;i++){
            unit.push_back(i);
            backtrack(k,n,i+1);
            unit.pop_back();
        }
    }
};

```

## Evaluation
![Combination Sum III](./02.png)