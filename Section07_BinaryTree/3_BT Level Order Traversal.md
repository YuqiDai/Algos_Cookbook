# Binay Tree Level Order Traversal
## Puzzle Description
Given the `root` of a binary tree, return *the level order traversal of its nodes' values*. (i.e., from left to right, level by level).

## Methodology
For deep ordered iterative binary tree traversal, we normally use `stack` to simulate the process of tree traversal. For level ordered iterative binary tree traversal, we normally use `queue` to simulate the process. Comparing iterative solution of binary tree traversal with recursive solution of binary tree traversal, it depends on the number of parameters we need to deliver in each ways to say which one is better.

## Code
1. Recursive Solution
```cpp
class Solution {
public:
    vector<vector<int>> levelOrder(TreeNode* root) {
        vector<vector<int>> ans;

        if(root!=nullptr){
            recursiveunit(root, 0, ans);
        }

        return ans;
    }

    void recursiveunit(TreeNode* node, int depth, vector<vector<int>>& ans){
        TreeNode* tp;

        if(node!=nullptr){
            if(ans.size()==depth){
                vector<int> line;
                ans.push_back(line);
            }

            ans[depth].push_back(node->val);
            recursiveunit(node->left, depth+1, ans);
            recursiveunit(node->right, depth+1, ans);
        }
    }
};
```

2. Iterative Solution
```cpp
class Solution {
public:
    vector<vector<int>> levelOrder(TreeNode* root) {
        vector<vector<int>> ans;
        queue<TreeNode*> que;
        TreeNode* tp=root;

        if(tp){
            que.push(tp);
        }

        while(!que.empty()){
            vector<int> line;
            int size=que.size();
            
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

            ans.push_back(line);
        }

        return ans;
    }
};
```

## Evaluation
1. For recursive solution    

![recursive](./3_recursive%20method.png)


2. For iterative solution     

![iterative](./3_iterative%20method.png)