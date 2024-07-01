# Three Consecutive Odds
## Link
[Three Consecutive Odds](https://leetcode.com/problems/three-consecutive-odds/)

## Code
```cpp
class Solution {
public:
    bool threeConsecutiveOdds(vector<int>& arr) {
        int num=0;
        for(int i=0;i<arr.size();++i){
            if(arr[i]%2!=0){
                ++num;
            }
            else{
                num=0;
            }
            
            if(num==3){
                return true;
            }
        }

        return false;
    }
};
```

## Evaluation
![Three Consecutive Odds](./03.PNG)