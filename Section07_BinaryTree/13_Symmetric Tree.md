# Symmetric Tree
## Link
[Symmetric Tree](https://leetcode.com/problems/symmetric-tree/description/)

## Code
```cpp
class Solution {
public:
    bool isSymmetric(TreeNode* root) {
        TreeNode* node=root;

        if(node){
            return core(node->left,node->right);
        }

        return false;
    }

    bool core(TreeNode* r1, TreeNode* r2){
        if(r1==nullptr&&r2==nullptr){
            return true;
        }
        if(r1==nullptr||r2==nullptr){
            return false;
        }
        if(r1->val==r2->val){
            return core(r1->left, r2->right)&&core(r1->right, r2->left);
        }

        return false;
    }

};
```

## Evaluation
![img](./13_img.PNG)