# Robot Collisions
## Link
[Robot Collisions](https://leetcode.com/problems/robot-collisions/description/)

## Code
```cpp
class Solution {
public:
    vector<int> survivedRobotsHealths(vector<int>& positions, vector<int>& healths, string directions) {
        int n=positions.size(), id[n];
        iota(id, id+n, 0);
        sort(id, id+n,[&](const int lf, const int rt){return positions[lf]<positions[rt];});
    
        stack<int> st;
        for(int i: id){
            if(directions[i]=='R'){
                st.push(i);
                continue;
            }

            while(!st.empty()){
                int top = st.top();
                if(healths[top] > healths[i]){
                    --healths[top];
                    healths[i] = 0;
                    break;
                }
                else if(healths[top]==healths[i]){
                    healths[top] = 0;
                    healths[i] = 0;
                    st.pop();
                    break;
                }
                else{
                    --healths[i];
                    healths[top] = 0;
                    st.pop();
                }
            }
        }

        healths.erase(remove(healths.begin(), healths.end(), 0), healths.end());

        return healths;
    }
};
```

## Evaluation
![Robot Collisions](./15.png)