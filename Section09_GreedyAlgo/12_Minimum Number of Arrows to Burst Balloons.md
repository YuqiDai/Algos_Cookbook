# Minimum Number of Arrows to Burst Balloons
## Link
[Minimum Number of Arrows to Burst Balloons](https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/description/)

## Code
```cpp
class Solution {
private:
    static bool cmp(const vector<int>& lf, const vector<int>& rt){
        if(lf[0]==rt[0])    return lf[1]<rt[1];
        return lf[0]<rt[0];
    }

public:
    int findMinArrowShots(vector<vector<int>>& points) {
        sort(points.begin(), points.end(), cmp);

        int num=1;

        for(int i=1;i<points.size();++i){
            if(points[i][0]>points[i-1][1]){
                ++num;
                continue;
            }
            else{
                points[i][1] = min(points[i-1][1], points[i][1]);
            }
        }

        return num;
    }
};
```

## Evaluation
![Minimum Number of Arrows to Burst Balloons](./12.PNG)