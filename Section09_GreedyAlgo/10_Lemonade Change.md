# Lemonade Change
## Link
[Lemonade Change](https://leetcode.com/problems/lemonade-change/description/)

## Code
```cpp
class Solution {
public:
    bool lemonadeChange(vector<int>& bills) {
        int f5=0,t10=0;

        for(int i=0;i<bills.size();++i){
            if(f5<0||t10<0){
                return false;
            }

            if(bills[i]==5){
                f5++;
            }
            else if(bills[i]==10){
                t10++;
                f5--;
            }
            else{
                if(t10>0){
                    t10--;
                    f5--;
                }
                else{
                    f5-=3;
                }
            }
        }

        return true;
    }
};
```

## Evaluation
![Lemonade Change](./10.png)