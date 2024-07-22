# Sort the People
## Link
[Sort the People](https://leetcode.com/problems/sort-the-people/description/)

## Code
```cpp
class Solution {
public:
    vector<string> sortPeople(vector<string>& names, vector<int>& heights) {
        map<int, string> mp;
        for(int i=0;i<names.size();++i){
            mp.insert({heights[i], names[i]});
        }

        stack<string> stk;
        map<int, string>::iterator it = mp.begin();

        while(it!=mp.end()){
            stk.push(it->second);
            it++;
        }

        vector<string> ans;
        while(!stk.empty()){
            ans.push_back(stk.top());
            stk.pop();
        }

        return ans;
    }
};
```

## Evaluation
![Sort the People](./18.PNG)