# Find Largest Value in Each Tree Row
## Puzzle Description
Given the `root` of a binary tree, return an array of the largest value in each row of the tree **(0-indexed)**.

## Methodology
Easy

## Code
```cpp
class Solution {
public:
    vector<int> largestValues(TreeNode* root) {
        vector<int> ans;
        TreeNode* tp=root;
        queue<TreeNode*> que;
        int size;

        if(tp){
            que.push(tp);
        }

        while(!que.empty()){
            size=que.size();
            vector<int> line;

            for(int i=0;i<size;i++){
                tp=que.front();
                que.pop();
                line.push_back(tp->val);

                if(tp->left){
                    que.push(tp->left);
                }
                if(tp->right){
                    que.push(tp->right);
                }
            }

            ans.push_back(findmax(line));
        }
        
        return ans;
    }

    int findmax(vector<int> line){
        int size=line.size();
        int max=line[0];
        for(int i=1;i<size;i++){
            if(max<line[i]){
                max=line[i];
            }
        }

        return max;
    }
};
```

## Evaluation
![img](./08_Find%20Largest%20Value%20in%20Each%20Tree%20Row.png)
