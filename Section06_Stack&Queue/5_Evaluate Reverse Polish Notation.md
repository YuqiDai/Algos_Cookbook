# Evaluate Reverse Polish Notation
## Puzzle Description
You are given an array of strings **tokens** that represents an arithmetic expression in a [Reverse Polish Notation](https://en.wikipedia.org/wiki/Reverse_Polish_notation).

Evaluate the expression. Return *an integer that represents the value of the expression*.

**Note** that:

* The valid operators are ***'+'***, ***'-'***, ***'\*'***, and ***'/'***.
* Each operand may be an integer or another expression.
* The division between two integers always **truncates toward zero**.
* There will not be any division by zero.
* The input represents a valid arithmetic expression in a reverse polish notation.
* The answer and all the intermediate calculations can be represented in a **32-bit** integer.

## Methodology
Refer to Code

## Code 
```c++
class Solution {
public:
    bool isOpt(std::string s){
        if(s.length()==1&&(s[0]=='+'||s[0]=='-'||s[0]=='*'||s[0]=='/')){
            return true;
        }
        else{
            return false;
        }
    }

    int cvt2int(std::string s){
        int len=s.length();
        int num=0;
        if(s[0]=='-')
        {
            for(int i=1;i<len;i++){
                int tp=(int)s[i]-48;
                for(int j=len-1-i;j>0;j--){
                    tp=tp*10;
                }
                num+=tp;
            }
            return -num;
        }
        for(int i=0;i<len;i++){
            int tp=(int)s[i]-48;
            for(int j=len-1-i;j>0;j--){
                tp=tp*10;
            }
            num+=tp;
        }
        return num;
    }

    int evalRPN(std::vector<std::string>& tokens) {
        std::stack<int> st;

        for(auto c:tokens){
            if(!isOpt(c)){
                int num=cvt2int(c);
                st.push(num);
            }   
            else{
                if(c[0]=='+'){
                    int ans;
                    int num1=st.top();
                    st.pop();
                    int num2=st.top();
                    st.pop();
                    ans=num1+num2;
                    st.push(ans);
                }
                else if(c[0]=='-'){
                    int ans;
                    int num1=st.top();
                    st.pop();
                    int num2=st.top();
                    st.pop();
                    ans=num2-num1;
                    st.push(ans);
                }
                else if(c[0]=='*'){
                    int ans;
                    int num1=st.top();
                    st.pop();
                    int num2=st.top();
                    st.pop();
                    ans=num1*num2;                
                    st.push(ans);

                }
                else{
                    int ans;
                    int num1=st.top();
                    st.pop();
                    int num2=st.top();
                    st.pop();
                    ans=num2/num1;
                    st.push(ans);
                }
            }
        }

        return st.top();
    }
};
```

## Evaluation
![img](./5_Evaluate%20Reverse%20Polish%20Notation.png)