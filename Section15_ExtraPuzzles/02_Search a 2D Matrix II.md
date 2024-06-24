# Search a 2D Matrix II
## Link
[Search a 2D Matrix II](https://leetcode.com/problems/search-a-2d-matrix-ii/description/)

## Code
```cpp
class Solution {
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target) {
        for(int i=matrix.size()-1,j=0;i<matrix.size()&&i>=0,j<matrix[0].size()&&j>=0;){
            if(matrix[i][j]>target){
                --i;
            }
            else if(matrix[i][j]<target){
                ++j;
            }
            else{
                return true;
            }
        }

        return false;
    }
};
```

## Evaluation
![Search a 2D Matrix II](./02.PNG)