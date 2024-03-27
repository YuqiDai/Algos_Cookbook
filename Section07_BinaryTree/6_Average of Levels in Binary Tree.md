# Average of Levels in Binary Tree
## Puzzle Description
Given the `root` of a binary tree, return *the average value of the nodes on each level in the form of an array*. Answers within $10^{-5}$ of the actual answer will be accepted.
## Methodology
Easy

## Code 
```cpp
class Solution {
public:
    vector<double> averageOfLevels(TreeNode* root) {
        vector<double> ans;
        TreeNode* tp=root;
        queue<TreeNode*> que;
        int size;

        if(tp){
            que.push(tp);
        }

        while(!que.empty()){
            size=que.size();
            double sum=0;

            for(int i=0;i<size;i++){
                tp=que.front();
                que.pop();

                sum+=tp->val;

                if(tp->left){
                    que.push(tp->left);
                }
                if(tp->right){
                    que.push(tp->right);
                }
            }

            ans.push_back(sum/size);
        }

        return ans;
    }
};
```

## Evaluation
![average](./6_Average%20of%20Levels%20in%20Binary%20Tree.png)