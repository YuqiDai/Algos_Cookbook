# Convert BST to Greater Tree
## Link
[Convert BST to Greater Tree](https://leetcode.com/problems/convert-bst-to-greater-tree/description/)

## Code
```cpp
class Solution {
public:
    TreeNode* convertBST(TreeNode* root) {
        if(root==nullptr) return root;
        
        int sum=0;
        core(root, sum);
        return root;
    }

    void core(TreeNode* node, int& sum){
        if(node==nullptr){
            return ;
        }

        core(node->right, sum);
        
        sum+=node->val;
        node->val = sum;
    
        core(node->left, sum);
    }
};
```

## Evaluation
![Convert BST to Greater Tree](./34_img.png)