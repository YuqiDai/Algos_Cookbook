# Number of 1 Bits
## Link
[Number of 1 Bits](https://leetcode.com/problems/number-of-1-bits/description/)

## Code
```cpp
class Solution {
public:
    int hammingWeight(int n) {
        int num=0;
        for(int i=0;i<32;++i){
            if(n&1){
                ++num;
            }
            n>>1;
        }
        return num;
    }
};

```

## Evaluation
![Number of 1 Bits](./08.png)