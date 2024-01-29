# Repeated Substring Pattern
## Puzzle Description
Given a string ***s***, check if it can be constructed by taking a substring of it and appending multiple copies of the substring together.

## Methodology
Refer to KMP and code section.

## Code
```cpp
class Solution {
public:
    bool repeatedSubstringPattern(std::string s) {
        int st[s.size()]={0};
        int j=0;
        for(int i=1;i<s.size();i++){
            while(j>0&&s[i]!=s[j]){
                j=st[j-1];
            }
            if(s[i]==s[j]){
                j++;
            }
            st[i]=j;
        }

        std::unordered_set<int> uset;
        for(int i=0;i<s.size();i++){
            uset.insert(st[i]);
        }
        for(auto tp: uset){
            if(tp==0){
                continue;
            }
            std::string unit="";
            std::string substr="";
            if(s.size()%tp==0){
                for(int i=0;i<tp;i++){
                    unit+=s[i];
                }
                for(int i=0;i<s.size()/tp;i++){
                    substr+=unit;
                }
                if(substr==s){
                    return true;
                }
            }
        }

        return false;
    }
};
```

## Evaluation
![img](./7_Repeated%20Substring%20Pattern.png)