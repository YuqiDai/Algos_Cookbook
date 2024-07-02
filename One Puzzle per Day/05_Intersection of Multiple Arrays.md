# Intersection of Multiple Arrays
## Link
[Intersection of Multiple Arrays](https://leetcode.com/problems/intersection-of-multiple-arrays/description/)

## Code
```cpp
class Solution {
public:
    vector<int> intersection(vector<vector<int>>& nums) {
        vector<int> ans = nums[0];
        
        if(nums.size()==1){
            sort(nums[0].begin(),nums[0].end());
            return nums[0];
        }

        map<int, int> mp;
        for(int i=0;i<nums[0].size();++i){
            mp[nums[0][i]]++;
        }

        for(int i=1;i<nums.size();++i){
            vector<int> tp;
            for(int j=0;j<nums[i].size();++j){
                if(mp.find(nums[i][j])!=mp.end()&&mp[nums[i][j]]>0){
                    tp.push_back(nums[i][j]);
                }
            }
            mp.clear();
            for(int k=0;k<tp.size();++k){
                mp[tp[k]]++;
            }
        }

        ans.clear();
        for(auto a:mp){
            while(a.second!=0){
                ans.push_back(a.first);
                a.second--;
            }
        }

        return ans;
    }
};
```

## Evaluation
![Intersection of Multiple Arrays](./05.PNG)