# Assign Cookies
## Link
[Assign Cookies](https://leetcode.com/problems/assign-cookies/)

## Code
```cpp
class Solution {
private:
    int num=0;
public:
    int findContentChildren(vector<int>& g, vector<int>& s) {
        sort(g.begin(), g.end());
        sort(s.begin(), s.end());

        for(int ig=0, is=0;ig<g.size()&&is<s.size();){
            if(g[ig]<=s[is]){
                ++ig;
                ++is;
                ++num;
            }
            else{
                ++is;
            }
        }

        return num;
    }
};
```

## Evaluation
![Assign Cookies](./01.png)