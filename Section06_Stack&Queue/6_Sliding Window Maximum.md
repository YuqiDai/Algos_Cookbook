# Sliding Window Maximum
## Puzzle Description
You are given an array of integers ***nums***, there is a sliding window of size ***k*** which is moving from the very left of the array to the very right. You can only see the ***k*** numbers in the window. Each time the sliding window moves right by one position.

Return *the max sliding window*.

## Methodology
The reason hard puzzle hard is because that it's very tough in both coming up with the solution and boundaries processing. For this sliding window maximum puzzle, you need to know a `queue` can be used as a data structure which could help form an ordered array. Because if you want to make the time complexity of this algorithm around `O(n)`, you need to have an ordered array.   

So talking about the method, please refer to [this link](https://github.com/youngyangyang04/leetcode-master/blob/master/problems/0239.%E6%BB%91%E5%8A%A8%E7%AA%97%E5%8F%A3%E6%9C%80%E5%A4%A7%E5%80%BC.md). The code given by them is quiet simplified, so for a better understading you can browse my code. After understanding how this method works, you can step to the code given by the link.

## Code 
1. A variant of O(n x m) algorithm, can reduce some time but not enough.
```c++
class Solution {
public:
    std::vector<int> maxSlidingWindow(std::vector<int>& nums, int k) {
        std::deque<int> dq;
        std::vector<int> ans;
        std::vector<int> maxList;
        int count=0, max=0;

        for(int i=0;i<k;i++){
            dq.push_back(nums[i]);
            if(max<nums[i]){
                max=nums[i];
                count=i;
            }
        }
        maxList.push_back(max);

        for(int i=k;i<nums.size();i++){
            count--;
            if(count>=0){
                if(max<nums[i]){
                    max=nums[i];
                    count=k-1;
                    dq.push_back(nums[i]);
                    dq.pop_front();
                    maxList.push_back(max);
                    continue;
                }
                else{
                    dq.push_back(nums[i]);
                    dq.pop_front();
                    maxList.push_back(max);
                    continue;                    
                }
            }
            else{
                max=-INT32_MAX;
                dq.push_back(nums[i]);
                dq.pop_front();
                for(int j=0;j<k;j++){
                    if(max<dq[j]){
                        max=dq[j];
                        count=j;
                    }
                }
                maxList.push_back(max);
            }
        }

        return maxList;
    }
};
```

2. Sliding window standard algorithm.
```cpp
class Solution {
public:
    std::vector<int> maxSlidingWindow(std::vector<int>& nums, int k) {
        std::deque<int> dq;
        std::vector<int> ans;
        
        dq.push_back(INT32_MIN);
        for(int i=0;i<k;i++){
            if(nums[i]>dq.front()){
                while(!dq.empty()){
                    dq.pop_front();
                }
                dq.push_back(nums[i]);
            }
            else{
                while(nums[i]>dq.back()){
                    dq.pop_back();
                }
                dq.push_back(nums[i]);
            }
        }
        ans.push_back(dq.front());

        for(int i=0;i<nums.size()-k;i++){
            if(nums[i]==dq.front()){
                dq.pop_front();
            }

            if(nums[i+k]>dq.front()){
                while(!dq.empty()){
                    dq.pop_front();
                }
                dq.push_back(nums[i+k]);
            }
            else{
                while(nums[i+k]>dq.back()){
                    dq.pop_back();
                }
                dq.push_back(nums[i+k]);
            }
            ans.push_back(dq.front());
        }

        return ans;
        
    }
};
```

## Evaluation
The evaluation image of method 2.

![img](./6_Sliding%20Window%20Maximum.png)