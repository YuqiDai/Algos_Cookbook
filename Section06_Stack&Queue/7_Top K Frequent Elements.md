# Top K Frequent Elements
## Puzzle Description
Given an integer array `nums` and an integer `k`, return *the `k` most frequent elements*. You may return the answer in **any order**.

## Methodology
Use `priority_queue` and `unordered_map` to solve it.

## Code 
```c++
class Solution {
public:
    class cmp{
    public:
            bool operator()(const std::pair<int,int>& lhs,  const std::pair<int,int>& rhs){
                return lhs.second > rhs.second;
            }
    };

    std::vector<int> topKFrequent(std::vector<int>& nums, int k) {
        std::vector<int> ans;
        std::unordered_map<int, int> mp;
        for(int i=0;i<nums.size();i++){
            mp[nums[i]]++;
        }

        std::priority_queue<std::pair<int,int>, std::vector<std::pair<int,int>>, std::less<int>> priq;

        for(std::unordered_map<int,int>::iterator it=mp.begin();it!=mp.end();it++){
            priq.push(*it);
            if(priq.size()>k){
                priq.pop();
            }
        }

        for(int i=0;i<k;i++){
            ans.push_back(priq.top().first);
            priq.pop();
        }

        return ans;
    }
};
```

## Evaluation
![img](./7_Top%20K%20Frequent%20Elements.png)