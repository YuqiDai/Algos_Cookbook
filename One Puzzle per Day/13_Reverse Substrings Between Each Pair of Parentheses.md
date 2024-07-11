# Reverse Substrings Between Each Pair of Parentheses
## Link
[Reverse Substrings Between Each Pair of Parentheses](https://leetcode.com/problems/reverse-substrings-between-each-pair-of-parentheses/description/)

## Code
```cpp
class Solution {
public:
    string reverseParentheses(string s) {
        if(s.size()==1){
            return s;
        }

        stack<char> st;
        stack<char> re;
        string tp="";
        string ans="";

        for(int i=0;i<s.size();++i){
            if(s[i]==')'){
                tp="";

                while(st.top()!='('){
                    tp+=st.top();
                    st.pop();
                }
                st.pop();

                for(int k=0;k<tp.size();++k){
                    st.push(tp[k]);
                }

                continue;
            }
            
            st.push(s[i]);
        }

        while(st.size()!=0){
            re.push(st.top());
            st.pop();
        }

        while(re.size()!=0){
            ans+=re.top();
            re.pop();
        }

        return ans;
    }
};
```

## Evaluation
![Reverse Substrings Between Each Pair of Parentheses](./13.PNG)