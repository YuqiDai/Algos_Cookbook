# Remove All Adjacent Duplicates In String
## Puzzle Description
You are given a string ***s*** consisting of lowercase English letters. A **duplicate removal** consists of choosing two **adjacent** and **equal** letters and removing them.

We repeatedly make **duplicate removals** on ***s*** until we no longer can.

Return *the final string after all such duplicate removals have been made*. It can be proven that the answer is **unique**.

## Methodology
Refer to puzzle 3 - "Valid Parentheses"

## Code 
```c++
class Solution {
public:
    std::string removeDuplicates(std::string s) {
        if(s.length()==0){
            return s;
        }

        std::stack<char> st;
        for(char c:s){
            if(st.empty()){
                st.push(c);
            }
            else{
                if(st.top()==c){
                    st.pop();
                }
                else{
                    st.push(c);
                }
            }
        }

        std::stack<char> bu;
        while(!st.empty()){
            bu.push(st.top());
            st.pop();
        }

        std::string ans;
        while(!bu.empty()){
            ans+=bu.top();
            bu.pop();
        }
        
        return ans;
    }
};
```

## Evaluation
![img](./4_Remove%20All%20Adjacent%20Duplicates%20In%20String.png)