# Reverse String II
## Puzzle Description
Given a string ***s*** and an integer ***k***, reverse the first ***k*** characters for every ***2k*** characters counting from the start of the string.    

If there are fewer than ***k*** characters left, reverse all of them. If there are less than ***2k*** but greater than or equal to ***k*** characters, then reverse the first ***k*** characters and leave the other as original.

## Methodology
**NOTICE**: ***Mind the boundary conditions***

## Code
```cpp
class Solution {
public:
    std::string reverseStr(std::string s, int k) {
        int len=s.size();
        int scal=len/(2*k);
        for(int i=0;i<scal*2*k;i+=2*k){
            int left=i,right=i+k-1;
            while(left<right){
                std::swap(s[left],s[right]);
                left++;
                right--;
            }
        }
        if(len-scal*2*k>k){
            int left=scal*2*k,right=scal*2*k+k-1;
            while(left<right){
                std::swap(s[left],s[right]);
                left++;
                right--;
            }
        }
        else{
            int left=scal*2*k, right=len-1;
            while(left<right){
                std::swap(s[left],s[right]);
                left++;
                right--;
            }
        }

        return s;
    }
};
```

## Evaluation
![img](./2_Reverse%20String%20II.png)