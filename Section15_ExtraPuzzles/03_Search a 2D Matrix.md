# Search a 2D Matrix
## Link
[Search a 2D Matrix](https://leetcode.com/problems/search-a-2d-matrix/)

## Code
```cpp
class Solution {
public:
    bool searchMatrix(vector<vector<int>>& matrix, int target) {
        for(int i=0;i<matrix.size();i++){
            for(int j=0;j<matrix[0].size();j++){
                if(target==matrix[i][j]) return true;
            }
        }
        return false;
    }
};
```

## Evaluation
![Search a 2D Matrix](./03.PNG)