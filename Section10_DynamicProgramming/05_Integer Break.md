# Integer Break
## Link
[Integer Break](https://leetcode.com/problems/integer-break/description/)

## Code
```cpp
class Solution {
public:
    int integerBreak(int n) {
        if(n==2) return 1;

        vector<int> dp(n, 1);

        for(int i=2;i<=n;++i){
            int fct = 1;
            vector<int> ary(i, n/i);
            for(int j=0;j<n%i;++j){
                ary[j]++;
            }
            for(int j=0;j<i;++j){
                fct*=ary[j];
            }
            dp.push_back(fct);
        }

        int mx=INT_MIN;
        for(int i=0;i<n;++i){
            if(mx<dp[i]) mx=dp[i];
        }

        return mx;
    }
};
```

## Evaluation
![Integer Break](./05.PNG)