# Water Bottles
## Link
[Water Bottles](https://leetcode.com/problems/water-bottles/description/)

## Code
```cpp
class Solution {
public:
    int numWaterBottles(int numBottles, int numExchange) {
        int sum=numBottles;
        int tp,left=0;

        while(numBottles>=numExchange){
            tp = numBottles/numExchange;
            left = numBottles%numExchange;
            sum+=tp;
            numBottles=tp+left;
        }

        return sum;
    }
};

```

## Evaluation
![Water Bottles](./10.png)