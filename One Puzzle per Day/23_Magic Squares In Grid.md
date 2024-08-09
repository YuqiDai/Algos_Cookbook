# Magic Squares In Grid
## Link
[Magic Squares In Grid](https://leetcode.com/problems/magic-squares-in-grid/)

## Code
```c++
class Solution
{
public:
    int numMagicSquaresInside(vector<vector<int>> &grid)
    {
        int row = grid.size();
        int col = grid[0].size();
        int sum = 0;

        for (int i = 0; i < row - 2; ++i)
        {
            for (int j = 0; j < col - 2; ++j)
            {
                set<int> st{1, 2, 3, 4, 5, 6, 7, 8, 9};
                for (int k = 0; k < 3; ++k)
                {
                    st.erase(grid[i][j + k]);
                    st.erase(grid[i + 1][j + k]);
                    st.erase(grid[i + 2][j + k]);
                }
                if (st.size() != 0)
                {
                    continue;
                }

                int sum1 = 0,
                    sum2 = 0,
                    sum3 = 0,
                    sum4 = 0,
                    sum5 = 0,
                    sum6 = 0,
                    sum7 = 0,
                    sum8 = 0;

                sum1 = grid[i][j] + grid[i][j + 1] + grid[i][j + 2];
                sum2 = grid[i + 1][j] + grid[i + 1][j + 1] + grid[i + 1][j + 2];
                sum3 = grid[i + 2][j] + grid[i + 2][j + 1] + grid[i + 2][j + 2];
                sum4 = grid[i][j] + grid[i + 1][j] + grid[i + 2][j];
                sum5 = grid[i][j + 1] + grid[i + 1][j + 1] + grid[i + 2][j + 1];
                sum6 = grid[i][j + 2] + grid[i + 1][j + 2] + grid[i + 2][j + 2];
                sum7 = grid[i][j] + grid[i + 1][j + 1] + grid[i + 2][j + 2];
                sum8 = grid[i][j + 2] + grid[i + 1][j + 1] + grid[i + 2][j];

                if (sum1 == sum2 && sum2 == sum3 && sum3 == sum4 && sum4 == sum5 && sum5 == sum6 && sum6 == sum7 && sum7 == sum8)
                {
                    ++sum;
                }
            }
        }

        return sum;
    }
};
```

## Evaluation
![Magic Squares In Grid](./23.png)