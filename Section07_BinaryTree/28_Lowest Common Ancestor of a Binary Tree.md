# Lowest Common Ancestor of a Binary Tree
## Link
[Lowest Common Ancestor of a Binary Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/description/)

## Code
```cpp
class Solution {
public:
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
        if(root==nullptr || root==p || root==q) return root;

        TreeNode* lf = lowestCommonAncestor(root->left, p, q);
        TreeNode* rt = lowestCommonAncestor(root->right, p, q);

        if(lf == nullptr) return rt;
        else if(rt == nullptr) return lf;
        return root;
    }
};
```

## Evaluation
![Lowest Common Ancestor of a Binary Tree](./28_img.png)