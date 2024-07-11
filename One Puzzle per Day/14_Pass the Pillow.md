# Pass the Pillow
## Link
[Pass the Pillow](https://leetcode.com/problems/pass-the-pillow/)

## Code
```cpp
class Solution {
public:
    int passThePillow(int n, int time) {
        if(time<n){
            return time+1;
        }
        else{
            int m = time/(n-1);
            if(m%2==0){
                return time%(n-1)+1;
            }
            else{
                return n-(time%(n-1));
            }
        }
    }
};
```

## Evaluation
![Pass the Pillow](./14.PNG)