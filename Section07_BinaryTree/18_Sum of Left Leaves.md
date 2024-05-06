# Sum of Left Leaves
## Link
[Sum of Left Leaves](https://leetcode.com/problems/sum-of-left-leaves/description/)

## Code
```cpp
class Solution {
public:
    int sumOfLeftLeaves(TreeNode* root) {
        if(root){
            return core(root);
        }

        return 0;
    }

    int core(TreeNode* node){
        if(node==nullptr){
            return 0;
        }

        if(node->left){
            if(node->left->left==nullptr&&node->left->right==nullptr){
                return node->left->val+core(node->right);
            }
        }

        return core(node->left)+core(node->right);
    }
};
```

## Evaluation
![img](./18_img.PNG)