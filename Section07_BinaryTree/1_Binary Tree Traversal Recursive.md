# Binary Tree Traversal
## Puzzle Description
Given the root of a binary tree, return the `preorder`/`postorder`/`inorder` traversal of its nodes' values.

## Methodology
Easy

## Code
```c++
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    vector<int> preorderTraversal(TreeNode* root) {
        vector<int> ans;

        if(root!=nullptr){
            ans.push_back(root->val);
            traverse(root->left, ans);
            traverse(root->right, ans);
        }

        return ans;
    }

    void traverse(TreeNode* node, vector<int>& ans){
        if(node!=nullptr){
            ans.push_back(node->val);
            traverse(node->left, ans);
            traverse(node->right, ans);
        }
    }
};
```

***NOTICE: I only give the code of binary tree preorder traversal, the other two are the same as this one.***

## Evaluation
![Binary Tree Preorder Traversal](./1_Binary%20Tree%20Traversal%20Recursive.png)







