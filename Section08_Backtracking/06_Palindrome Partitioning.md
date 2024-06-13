# Palindrome Partitioning
## Link
[Palindrome Partitioning](https://leetcode.com/problems/palindrome-partitioning/description/)

## Code
```cpp
class Solution {
private:
    vector<string> unit;
    vector<vector<string>> ans;

    bool checkPalindrome(string s){
        int lf=0, rt=s.size()-1;
        while(lf<=rt){
            if(s[lf]!=s[rt]){
                return false;
            }

            lf++;
            rt--;
        }

        return true;
    }

    void backtrack(string s, int lenOfOriString){
        if(s.size()==1){
            unit.push_back(s);
            ans.push_back(unit);
            unit.pop_back();
            return ;
        }
        if(checkPalindrome(s)){
            unit.push_back(s);
            ans.push_back(unit);
            unit.pop_back();
        }

        for(int i=1;i<s.size();i++){
            string s1(s.begin(), s.begin()+i);
            string s2(s.begin()+i, s.end());
            if(checkPalindrome(s1)){
                unit.push_back(s1);
            }
            else{
                continue;
            }

            backtrack(s2, lenOfOriString);
            unit.pop_back();
        }
    }

public:
    vector<vector<string>> partition(string s) {
        int lenOfOriString = s.size();
        backtrack(s, lenOfOriString);
        return ans;
    }

};
```

## Evaluation
![Palindrome Partitioning](./06.PNG)