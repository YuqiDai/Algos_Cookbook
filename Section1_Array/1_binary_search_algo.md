# ***Binary Search***
## Puzzle Description
Given a  ***n*** sorted (ascending) integer array of elements  ***nums*** and a target value  ***target***  , write a function that  ***nums*** returns ***target*** the index if the target value exists, otherwise returns ***-1***.   
Refer to [Leetcode BinarySearch](https://leetcode.cn/problems/binary-search/).

## Methodology
Since we need the index of the target existing in the array, Use recursion function to solve this puzzle will be complicated. So there we use a simple ***while*** loop.      

## Code
```c++
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int left, right;
        left=0; right=nums.size()-1;

        while(left<=right){
            int mid=(left+right)/2;
            
            if(nums[mid]==target){
                return mid;
            }
            else if(nums[mid]>target){
                right=mid-1;
                continue;
            }
            else{
                left=mid+1;
                continue;
            }
        }
        
        return -1;
    }
};
```

## Evaluation
![img](./binary_search.png)   

Remark: This evaluation depends on the population using the server you commiting your code. But you can refer to this as one of the standards of good algorithms.
