# Jump Game II
## Link
[Jump Game II](https://leetcode.com/problems/jump-game-ii/description/)

## Code
```cpp
class Solution {
public:
    int jump(vector<int>& nums) {
        int lf=0, rt=lf+nums[lf];
        int num=1;
        if(nums.size()==1){
            return 0;
        }
        while(rt<nums.size()-1){
            int m=INT_MIN,index;
            for(;lf<=rt;++lf){
                if(m<=lf+nums[lf]){
                    m=lf+nums[lf];
                    index=lf;
                }
            }
            rt=m;
            lf=index;
            ++num;
        }

        return num;
    }
};
```

## Evaluation
![Jump Game II](./06.PNG)