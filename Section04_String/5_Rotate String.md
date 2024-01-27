# Rotate String
## Puzzle Description
Given two strings ***s*** and ***goal***, return ***true*** if and only if ***s*** can become ***goal*** after some number of **shifts** on ***s***.

A **shift** on ***s*** consists of moving the leftmost character of ***s*** to the rightmost position.

For example, if ***s = "abcde"***, then it will be **"bcdea"** after one shift.

## Methodology
Easy, no need to give a methodology.

## Code
```cpp
class Solution {
public:
    bool rotateString(std::string s, std::string goal) {
        int len=s.size();
        int flag=0;

        for(int i=0;i<len;i++){
            flag=0;
            int k=0;
            for(int j=i+1;j<len;j++){
                if(goal[k]==s[j]){
                    k++;
                    continue;
                }
                else{
                    flag=-1;
                    break;
                }
            }
            if(flag==-1){
                continue;
            }
            for(int m=0;m<=i;m++){
                if(goal[k]==s[m]){
                    k++;
                    continue;
                }
                else{
                    flag=-1;
                    break;
                }
            }
            if(flag==-1){
                continue;
            }
            else{
                return true;
            }
        }

        return false;
    }
};
```

## Evaluation
![img](./5_Rotate%20String.png)