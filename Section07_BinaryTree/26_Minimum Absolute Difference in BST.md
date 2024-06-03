# Minimum Absolute Difference in BST
## Link
[Minimum Absolute Difference in BST](https://leetcode.com/problems/minimum-absolute-difference-in-bst/description/)

## Code
```cpp
class Solution {
public:
    int getMinimumDifference(TreeNode* root) {
        int pre=-1;
        int ans=INT_MAX;
        core(root, pre, ans);
        
        return ans;
    }
    
    void core(TreeNode* node, int& pre, int& ans){
        if(node==nullptr){
            return ;
        }

        core(node->left, pre, ans);
        if(pre!=-1){
            ans = ans<(node->val - pre)?ans:(node->val - pre);
        }
        pre = node->val;
        core(node->right, pre, ans);
    }
};
```

## Evaluation
![Minimum Absolute Difference in BST](./26_img.png)