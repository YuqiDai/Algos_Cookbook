# Climbing Stairs
## Link
[Climbing Stairs](https://leetcode.com/problems/climbing-stairs/description/)

## Code
```cpp
class Solution {
public:
    unordered_map<int, int> used;

    int core(int n){
        if(n==0||n==1){
            return 1;
        }

        if(used.find(n)==used.end()){
            used[n] = core(n-1)+core(n-2);
        }

        return used[n];

    }

    int climbStairs(int n) {
        return core(n);
    }
};
```

## Evaluation
![Climbing Stairs](./05.PNG)