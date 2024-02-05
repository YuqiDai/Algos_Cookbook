# Valid Parentheses
## Puzzle Description
Given a string ***s*** containing just the characters ***'('***, ***')'***, ***'{'***, ***'}'***, ***'['*** and ***']'***, determine if the input string is valid.

An input string is valid if:

1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.
3. Every close bracket has a corresponding open bracket of the same type.

## Methodology
If -> the length of string is odd, return false;   
Else -> if the first character is ')' or ']' or '}', return false;
Else -> use stack to determine whether the string is valid.

## Code
```c++
class Solution {
public:
    bool isValid(std::string s) {
        if(s.size()%2!=0){
            return false;
        }
        if(s[0]==')'
        ||s[0]==']'
        ||s[0]=='}'){
            return false;
        }

        std::stack<char> st;
        for(auto a:s){
            if(st.empty()){
                st.push(a);
            }
            else{
                if((((int)st.top()-(int)a)==-1)||((int)st.top()-(int)a)==-2){
                    st.pop();
                }
                else{
                    st.push(a);
                }
            }
        }

        if(st.empty()){
            return true;
        }
        else{
            return false;
        }
    }
};
```

## Evaluation
![img](./3_Valid%20Parentheses.png)

