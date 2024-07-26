# Find the City With the Smallest Number of Neighbors at a Threshold Distance
## Link
[Find the City With the Smallest Number of Neighbors at a Threshold Distance](https://leetcode.com/problems/find-the-city-with-the-smallest-number-of-neighbors-at-a-threshold-distance)

## Code
```cpp
class Solution {
public:
    int findTheCity(int n, vector<vector<int>>& edges, int distanceThreshold) {
        vector<vector<vector<int>>> dp(n+1, vector<vector<int>>(n+1, vector<int>(n+1,10004)));

        for(int i=0;i<edges.size();++i){
            dp[edges[i][0]+1][edges[i][1]+1][0]=edges[i][2];
            dp[edges[i][1]+1][edges[i][0]+1][0]=edges[i][2];
        }

        for(int k=1;k<=n;++k){
            for(int i=1;i<=n;++i){
                for(int j=1;j<=n;++j){
                    dp[i][j][k] = min(dp[i][j][k-1], dp[i][k][k-1] + dp[k][j][k-1]);     
                }
            }
        }

        vector<int> ans(n, 0);
        for(int i=1;i<=n;++i){
            for(int j=1;j<=n;++j){
                if(i==j) continue;
                if(dp[i][j][n]<=distanceThreshold){
                    ans[i-1]++;
                }
            }
        }

        int mx=INT_MAX, index;
        for(int i=0;i<n;++i){
            if(mx>=ans[i]){
                mx=ans[i];
                index=i;
            }
        }

        return index;
    }
};
```

## Evaluation
![Find the City With the Smallest Number of Neighbors at a Threshold Distance](./21.PNG)