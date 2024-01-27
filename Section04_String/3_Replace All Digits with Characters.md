# Replace All Digits with Characters
## Puzzle Description
You are given a **0-indexed** string ***s*** that has lowercase English letters in its **even** indices and digits in its **odd** indices.

There is a function ***shift(c, x)***, where ***c*** is a character and ***x*** is a digit, that returns the $x^{th}$ character after c.

For example, ***shift('a', 5) = 'f'*** and ***shift('x', 0) = 'x'***.
For every **odd** index ***i***, you want to replace the digit ***s[i]*** with ***shift(s[i-1], s[i])***.

Return ***s*** after replacing all digits. It is ***guaranteed*** that ***shift(s[i-1], s[i])*** will never exceed 'z'.

## Methodology
1. Noomb method which is the one I submit. Use modulo to find odd indices, then use binary search algo to find the position ***s[i-1]*** in alphabeta table. Then find the ***s[i-1]+s[i]-48*** and replace ***s[i]*** with it. Noomb and slow.

2. Brilliant one. Use binary operations. Easy and fast as be shown in code.


## Code
1. Noomb one
```cpp
int binarysearch(std::string s, char a){
    int len=s.size();
    int left=0,right=len-1;

    while(left<=right){
        if(s[(left+right)/2]==a){
            return (left+right)/2;
        }
        else if(s[(left+right)/2]<a){
            left=(left+right)/2+1;
        }
        else{
            right=(left+right)/2-1;
        }
    }

    return -1;
}

class Solution {
public:
    std::string replaceDigits(std::string s) {
        std::string ltr="abcdefghijklmnopqrstuvwxyz";
        int len=s.size();
        for(int i=0;i<len;i++){
            if(i%2==1){
                int index=binarysearch(ltr,s[i-1]);
                index+=(int)s[i]-48;
                s[i]=ltr[index];
            }
        }
        return s;
    }
};
```

2. Brilliant one
```c++
class Solution {
public:
    string replaceDigits(string s) {
       for(int i =1; i <s.length(); i=i+2)
       s[i] += s[i-1] -'0';
       return s; 
    }
};
```

## Evaluation
1. Noomb one
![img](./3_Replace%20All%20Digits%20with%20Characters_1.png)
2. Brilliant one
![img](./3_Replace%20All%20Digits%20with%20Characters_2.png)