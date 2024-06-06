# Trim a Binary Search Tree
## Link
[Trim a Binary Search Tree](https://leetcode.com/problems/trim-a-binary-search-tree/description/)

## Code
```cpp
class Solution {
public:
    TreeNode* trimBST(TreeNode* root, int low, int high) {
        if(root==nullptr){
            return root;
        }

        if(root->val<low){
            return trimBST(root->right, low, high);
        }
        else if(root->val>high){
            return trimBST(root->left, low, high);
        }

        core(root->left, low, high, root);
        core(root->right, low, high, root);

        return root;
    }

    void core(TreeNode* node, int low, int high, TreeNode* prev){
        if(node==nullptr){
            return ;
        }

        if(node->val<low){
            // move the left kid tree
            prev->left = node->right;
            core(prev->left, low, high, prev);
        }
        else if(node->val>high){
            // move the right kid tree
            prev->right = node->left;
            core(prev->right, low, high, prev);
        }

        core(node->left, low, high, node);
        core(node->right, low, high, node);
    }
};
```

## Evaluation
![img](./32_img.png)