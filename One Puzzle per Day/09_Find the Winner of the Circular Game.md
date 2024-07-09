# Find the Winner of the Circular Game
## Link
[Find the Winner of the Circular Game](https://leetcode.com/problems/find-the-winner-of-the-circular-game/description)

## Code
```cpp
class Solution {
public:
    int findTheWinner(int n, int k) {
        if(n==1){
            return 1;
        }

        vector<int> circle(n);
        for(int i=0;i<circle.size();++i){
            circle[i]=i+1;
        }

        int alive=n;
        int ptr=0;

        while(alive!=1){
            ptr=(ptr+k-1)%alive;
            circle.erase(circle.begin()+ptr);
            --alive;
        }

        return circle[0];
    }
};
```

## Evaluation
![Find the Winner of the Circular Game](./09.png)