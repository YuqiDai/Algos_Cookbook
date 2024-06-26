# Assign Cookies
## Link
[Assign Cookies](https://leetcode.com/problems/assign-cookies/description/)

## Code
```cpp
class Solution {
public:
    int findContentChildren(vector<int>& g, vector<int>& s) {
        sort(g.begin(),g.end());
        sort(s.begin(),s.end());

        int i=0,j=0,num=0;
        while(i<g.size()&&j<s.size()){
            if(g[i]<=s[j]){
                ++i,++j,++num;
                continue;
            }
            else{
                ++j;
            }
        }

        return num;
    }
};
```

## Evaluation
![Assign Cookies](./06.PNG)