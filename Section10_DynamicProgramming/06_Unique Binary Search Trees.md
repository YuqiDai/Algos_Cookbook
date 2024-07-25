# Unique Binary Search Trees
## Link
[Unique Binary Search Trees](https://leetcode.com/problems/unique-binary-search-trees/)

## Code
```cpp
class Solution {
public:
    int numTrees(int n) {
        vector<int> dp(n+1, 0);
        if(n<0) return -1;
        if(n==1||n==0) return 1;
        dp[0]=1;

        for(int i=1;i<=n;++i){
            for(int j=1;j<=i;++j){
                dp[i]+=dp[j-1]*dp[i-j];
            }
        }

        return dp[n];
    }
};
```

## Evaluation
![Unique Binary Search Trees](./06.PNG)