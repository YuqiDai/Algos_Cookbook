# Lowest Common Ancestor of a Binary Search Tree
## Link
[Lowest Common Ancestor of a Binary Search Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/description/)

## Code
```cpp
class Solution {
public:
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
        if(root==nullptr) return root;

        TreeNode* lf = lowestCommonAncestor(root->left, p, q);
        if(p->val <= q->val){
            if(root->val>=p->val && root->val<=q->val) return root;
        }
        else{
            if(root->val>=q->val && root->val<=p->val) return root;
        }
        TreeNode* rt = lowestCommonAncestor(root->right, p, q);

        if(lf==nullptr) return rt;
        return lf;
    }
};
```

## Evaluation
![Lowest Common Ancestor of a Binary Search Tree](./29_img.png)