# Min Cost Climbing Stairs
## Link
[Min Cost Climbing Stairs](https://leetcode.com/problems/min-cost-climbing-stairs/)

## Code
```cpp
class Solution {
public:
    int minCostClimbingStairs(vector<int>& cost) {
        vector<int> dp(cost.size()+1, 0);

        for(int i=2;i<=cost.size();++i){
            dp[i] = min(dp[i-2]+cost[i-2], dp[i-1]+cost[i-1]);
        }

        return dp[cost.size()];
    }
};
```

## Evaluation
![Min Cost Climbing Stairs](./02.PNG)