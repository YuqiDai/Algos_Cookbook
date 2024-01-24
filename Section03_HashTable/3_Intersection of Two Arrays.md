# Intersection of Two Arrays

## Puzzle Description
Given two integer arrays ***nums1*** and ***nums2***, return an array of their intersection. Each element in the result must be **unique** and you may return the result in **any order**.

## Methodology
Refer to the code. There are two options to choose.

## Code 
1. Faster than ever, but use a little bit more memory.
```c++
class Solution {
public:
    std::vector<int> intersection(std::vector<int>& nums1, std::vector<int>& nums2) {
        std::vector<int> ans;
        int a[1000]={0};
        for(auto ir: nums1){
            a[ir]=1;
        }
        for(auto ir: nums2){
            if(a[ir]==1){
                a[ir]++;
            }
            else{
                continue;
            }
        }
        for(int i=0;i<1000;i++){
            if(a[i]>=2){
                ans.push_back(i);
            }
        }

        return ans;
    }
};
```

2. Using hash table, easy to cook up.
```c++
class Solution {
public:
    std::vector<int> intersection(std::vector<int>& nums1, std::vector<int>& nums2) {
        std::vector<int> ans;
        std::unordered_set<int> uset1,uset2;
        for(auto a: nums1){
            uset1.insert(a);
        }
        for(auto b: nums2){
            uset2.insert(b);
        }
        for(int a: uset1){
            if(uset2.find(a)!=uset2.end()){
                ans.push_back(a);
            }
        }

        return ans;
    }
};
```

## Evaluation
1. Option 1
![Option 1](./3_Intersection%20of%20Two%20Arrays.png)
2. Option 2
![Option 2](./3_Intersection%20of%20Two%20Arrays%20(2).png)