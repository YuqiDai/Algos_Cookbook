# Validate Binary Search Tree
## Link
[Validate Binary Search Tree](https://leetcode.com/problems/validate-binary-search-tree/description/)

## Code
```cpp
class Solution {
public:
    bool isValidBST(TreeNode* root) {
        return core(root, LONG_MIN, LONG_MAX);
    }

    bool core(TreeNode* node, long min, long max){
        if(node){
            if(node->val<=min||node->val>=max){
                return false;
            }

            return core(node->left, min, node->val)&&core(node->right, node->val, max);
        }

        return true;
    }
};
```

## Evaluation
![img](./25_img.PNG)