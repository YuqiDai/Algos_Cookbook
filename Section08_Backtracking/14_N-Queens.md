# N-Queens
## Link
[N-Queens](https://leetcode.com/problems/n-queens/description/)

## Code
```cpp
class Solution {
private:
    vector<string> unit;
    vector<vector<string>> ans;

    bool checkQ(int x, int y, int n){
        if(unit.size()==0){
            return true;
        }

        for(int i=x-1,j=y;i>=0;i--){
            if(unit[i][j]=='Q'){
                return false;
            }
        }

        for(int i=x-1, j=y-1; i>=0&&j>=0; --i,--j){
            if(unit[i][j]=='Q'){
                return false;
            }
        }

        for(int i=x-1, j=y+1; i>=0&&j<=n; --i,++j){
            if(unit[i][j]=='Q'){
                return false;
            }
        }

        return true;
    }

    void bt(int n, int index){
        if(index==n){
            ans.push_back(unit);
            return ;
        }

        for(int y=0;y<n&&index<n;y++){
            if(checkQ(index, y, n)){
                string s="";
                for(int k=0;k<n;k++){
                    if(k==y){
                        s.push_back('Q');
                    }
                    else{
                        s.push_back('.');
                    }
                }
                unit.push_back(s);
                bt(n, index+1);
                unit.pop_back();
            }
        }
    }
public:
    vector<vector<string>> solveNQueens(int n) {
        bt(n, 0);
        return ans;
    }
};
```

## Evaluation
![N-Queens](./14.png)