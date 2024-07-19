# Lucky Numbers in a Matrix
## Link
[Lucky Numbers in a Matrix](https://leetcode.com/problems/lucky-numbers-in-a-matrix/)

## Code
```cpp
class Solution {
public:
    vector<int> luckyNumbers (vector<vector<int>>& matrix) {
        vector<int> ans;

        for(int i=0;i<matrix.size();++i){
            int min_row=INT_MAX, col=0;
            for(int j=0;j<matrix[i].size();++j){
                if(matrix[i][j]<min_row){
                    min_row = matrix[i][j];
                    col = j;
                }
            }
            
            int max_col=matrix[i][col], flag=0;
            for(int k=0;k<matrix.size();++k){
                if(max_col<matrix[k][col]){
                    flag=1;
                }
            }
            if(flag==0){
                ans.push_back(max_col);
            }
        }

        return ans;
    }
};
```

## Evaluation
![Lucky Numbers in a Matrix](./17.PNG)