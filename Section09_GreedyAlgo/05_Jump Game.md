# Jump Game
## Link
[Jump Game](https://leetcode.com/problems/jump-game/)

## Code
```cpp
class Solution {
public:
    bool canJump(vector<int>& nums) {
        int lf=0,rt=lf+nums[lf];
        int pre=0;
        while(rt<nums.size()-1){
            if(rt==pre){
                return false;
            }
            int m=INT_MIN, index;
            for(;lf<=rt;++lf){
                if(m<=lf+nums[lf]){
                    m=lf+nums[lf];
                    index=lf;
                }
            }
            pre=rt;
            rt=m;
            lf=index;
        }

        return true;
    }
};
```

## Evaluation
![Jump Game](./05.PNG)