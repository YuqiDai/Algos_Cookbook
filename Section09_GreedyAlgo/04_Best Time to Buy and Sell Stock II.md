# Best Time to Buy and Sell Stock II
## Link
[Best Time to Buy and Sell Stock II](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/description/)

## Code
```cpp
class Solution {
private:
    int sum=0;
public:
    int maxProfit(vector<int>& prices) {
        for(int i=0;i<prices.size()-1;++i){
            while(i<prices.size()-1){
                if(prices[i+1]>prices[i]){
                    break;
                }
                ++i;
                
                if(i>=prices.size()-1){
                    return sum;
                }
            }

            if(prices[i+1]>prices[i]){
                sum+=(prices[i+1]-prices[i]);
                continue;
            }

        }

        return sum;
    }
};
```

## Evaluation
![Best Time to Buy and Sell Stock II](./04.png)