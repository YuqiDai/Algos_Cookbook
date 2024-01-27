# Reverse Words in a String
## Puzzle Description
Given an input string ***s***, reverse the order of the **words**.

A **word** is defined as a sequence of non-space characters. The **words** in ***s*** will be separated by at least one space.

Return *a string of the words in reverse order concatenated by a single space*.

**Note** that ***s*** may contain leading or trailing spaces or multiple spaces between two words. The returned string should only have a single space separating the words. Do not include any extra spaces.

## Methodology
Easy, no methodology.


## Code
```cpp
class Solution {
public:
    std::string reverseWords(std::string s) {
        std::vector<std::string> str;
        std::string tp;
        for(int i=0;i<s.size();i++){
            if(s[i]==' '){
                if(tp!=""){
                    str.push_back(tp);
                    tp.clear();
                }
                continue;
            }
            else{
                tp+=s[i];
            }
        }
        if(tp!=""){
            str.push_back(tp);
        }

        std::reverse(str.begin(),str.end());
        std::string ans;
        for(int i=0;i<str.size()-1;i++){
            ans+=str[i]+" ";
        }
        
        ans=ans+str[str.size()-1];

        return ans;
    }
};
```

## Evaluation
![img](./4_Reverse%20Words%20in%20a%20String.png)