# Number of Good Leaf Nodes Pairs
## Link
[Number of Good Leaf Nodes Pairs](https://leetcode.com/problems/number-of-good-leaf-nodes-pairs/)

## Code
```cpp
class Solution {
private:
    vector<int> core(TreeNode* node, int distance, int& sum){
        if(!node->left&&!node->right){
            return {1};
        }

        vector<int> lf, rt, ret;

        if(node->left)  lf = core(node->left, distance, sum);
        if(node->right) rt = core(node->right, distance, sum);

        for(auto i: lf){
            for(auto j:rt){
                if(i+j <= distance){
                    sum++;
                }
            }
        }
        for(auto i:lf){
            i++;
            if(i<distance){
                ret.push_back(i);
            }
        }
        for(auto j:rt){
            j++;
            if(j<distance){
                ret.push_back(j);
            }
        }

        return ret;
    }

public:
    int countPairs(TreeNode* root, int distance) {
        int sum=0;
        core(root, distance, sum);
        return sum;
    }
};
```

## Evaluation
![Number of Good Leaf Nodes Pairs](./16.PNG)