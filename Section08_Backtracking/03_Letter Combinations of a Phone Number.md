# Letter Combinations of a Phone Number
## Link
[Letter Combinations of a Phone Number](https://leetcode.com/problems/letter-combinations-of-a-phone-number/description/)

## Code
```cpp
class Solution {
private:
    vector<string> num2c{"abc", "def", "ghi", "jkl", "mno", "pqrs", "tuv", "wxyz"};
    vector<string> ans;
    string s;
public:
    int c2index(char c){
        return (int)c - 50;
    }

    vector<string> letterCombinations(string digits) {
        if(digits.size()==0){
            return ans;
        }

        backtrack(digits, 0);
        return ans;
    }

    void backtrack(string digits, int index){
        if(s.size()==digits.size()){
            ans.push_back(s);
            return ;
        }

        for(int j=0;j<num2c[c2index(digits[index])].size();j++){
            s.push_back(num2c[c2index(digits[index])][j]);
            backtrack(digits, index+1);
            s.pop_back();
        }
    }
};

```

## Evalutaion
![Letter Combinations of a Phone Number](./03.png)