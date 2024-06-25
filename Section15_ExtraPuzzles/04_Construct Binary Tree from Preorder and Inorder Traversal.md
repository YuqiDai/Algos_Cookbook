# Construct Binary Tree from Preorder and Inorder Traversal
## Link
[Construct Binary Tree from Preorder and Inorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/description/)

## Code
```cpp
struct TreeNode {
    int val;
    TreeNode *left;
    TreeNode *right;
    TreeNode() : val(0), left(nullptr), right(nullptr) {}
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
    TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
};
 
class Solution {
private: 
    int preindex=0;
    TreeNode* core(vector<int>& preorder, vector<int>& inorder, int in_lf, int in_rt){
        if(in_lf>in_rt){
            return nullptr;
        }

        int tp=in_lf;
        while(tp<=in_rt){
            if(preorder[preindex]==inorder[tp]){
                break;
            }
            ++tp;
        }

        TreeNode* newNode = new TreeNode(preorder[preindex++]);

        newNode->left = core(preorder, inorder, in_lf, tp-1);
        newNode->right = core(preorder, inorder, tp+1, in_rt);

        return newNode;
    }

public:
    TreeNode* buildTree(vector<int>& preorder, vector<int>& inorder) {
        TreeNode* root = new TreeNode(preorder[preindex++]);

        int tp=0;
        while(tp<inorder.size()){
            if(preorder[0]==inorder[tp]){
                break;
            }
            ++tp;
        }
        root->left = core(preorder, inorder, 0, tp-1);
        root->right = core(preorder, inorder, tp+1, inorder.size()-1);

        return root;
    }
};
```

## Evaluation
![Construct Binary Tree from Preorder and Inorder Traversal](./04.PNG)