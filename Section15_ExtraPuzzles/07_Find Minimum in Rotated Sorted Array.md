# Find Minimum in Rotated Sorted Array
## Link
[Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/description/)

## Code
```cpp
class Solution {
public:
    int findMin(vector<int>& nums) {
        int lf=0, rt=nums.size()-1;

        while(lf<=rt){
            if(lf==rt){
                return nums[lf];
            }
            if(rt-lf==1){
                return min(nums[lf], nums[rt]);
            }

            if(nums[lf]<nums[(lf+rt)/2]&&nums[(lf+rt)/2+1]<nums[rt]){
                return nums[(lf+rt)/2+1];
            }

            if(nums[lf]>nums[(lf+rt)/2]){
                rt=(lf+rt)/2;
            }
            else{
                lf=(lf+rt)/2+1;
            }
        }

        return -1;
    }
};

```

## Evaluation
![Find Minimum in Rotated Sorted Array](./07.png)