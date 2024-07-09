# Candy
## Link
[Candy](https://leetcode.com/problems/candy/description/)

## Code
```cpp
class Solution {
public:
    int candy(vector<int>& ratings) {
        vector<int> ary(ratings.size(), 1);
        
        for(int i=0;i<ratings.size()-1;++i){
            if(ratings[i]<ratings[i+1]){
                ary[i+1]=ary[i]+1;
            }
        }

        for(int i=ratings.size()-1;i>0;--i){
            if(ratings[i-1]>ratings[i]){
                ary[i-1]=max(ary[i-1],ary[i]+1);
            }
        }

        int sum=0;
        for(int i=0;i<ary.size();++i){
            sum+=ary[i];
        }

        return sum;
    }
};
```

## Evaluation
![Candy](./09.png)