# Sort the Jumbled Numbers
## Link
[Sort the Jumbled Numbers](https://leetcode.com/problems/sort-the-jumbled-numbers/)

## Code
```cpp
class Solution {
private:
    static inline bool cmp(vector<int> a, vector<int> b){
        return a[0]<b[0];
    }
public:
    vector<int> sortJumbled(vector<int>& mapping, vector<int>& nums) {
        vector<string> vs;
        vector<int> ans;
        vector<vector<int>> mid;
        
        for(int i=0;i<nums.size();++i){
            vs.push_back(to_string(nums[i]));
        }


        for(int i=0;i<vs.size();++i){
            string tp="";
            for(int j=0;j<vs[i].size();++j){
                tp.push_back((char)(mapping[(int)vs[i][j]-48]+48));
            }
            vs[i]=tp;
        }

        for(int i=0;i<vs.size();++i){
            ans.push_back(stoi(vs[i]));
        }

        for(int i=0;i<vs.size();++i){
            mid.push_back({ans[i], nums[i]});
        }

        sort(mid.begin(), mid.end(), cmp);

        for(int i=0;i<mid.size();++i){
            ans[i] = mid[i][1];
        }

        return ans;
    }
};
```

## Evaluation
![Sort the Jumbled Numbers](./19.PNG)