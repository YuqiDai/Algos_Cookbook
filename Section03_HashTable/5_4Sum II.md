# 4Sum II
## Puzzle Description
Given four integer arrays ***nums1***, ***nums2***, ***nums3***, and ***nums4*** all of length ***n***, return the number of tuples ***(i, j, k, l)*** such that:   
* $0 <= i, j, k, l < n$
* $nums1[i] + nums2[j] + nums3[k] + nums4[l] == 0$

## Methodology
If we use 4 loops to compute the result then compare it with 0, the time complexity will be $O(n^4)$, it's pretty high. So we combine two vectors into one (i.e. put nums1&nums2 together as newnums1, put nums3&nums4 together as newnums2). Before next step, we need to know that proving $a + b = c$ is equal to prove $b = c-a$. The latter equation focuses on the existance of variable ***b***. So we can use hashtable to store all the ***a*** after our computing, the hashtable can also be used to prove the existance of ***b***, because $a = c - b$.

## Code
```cpp
class Solution {
public:
    int fourSumCount(std::vector<int>& nums1, std::vector<int>& nums2, std::vector<int>& nums3, std::vector<int>& nums4) {
        std::unordered_map<int,int> mp;
        int ans=0;

        for(auto i: nums1){
            for(auto j: nums2){
                mp[i+j]++;
            }
        }

        for(auto i: nums3){
            for(auto j: nums4){
                if(mp.count(-i-j)){
                    ans+=mp[-i-j];
                }
            }
        }

        return ans;
    }
};
```

## Evaluation
![img](./5_4Sum%20II.png)
