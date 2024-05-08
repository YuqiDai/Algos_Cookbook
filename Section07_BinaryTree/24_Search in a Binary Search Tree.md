# Search in a Binary Search Tree
## Link
[Search in a Binary Search Tree](https://leetcode.com/problems/search-in-a-binary-search-tree/description/)

## Code
```cpp
class Solution {
public:
    TreeNode* searchBST(TreeNode* root, int val) {
        return core(root, val);
    }

    TreeNode* core(TreeNode* node, int val){
        if(node){
            if(val==node->val){
                return node;
            }
            if(val>node->val){
                return core(node->right, val);
            }
            else{
                return core(node->left, val);
            }
        }

        return nullptr;
    }
};
```

## Evaluation
![img](./24_img.PNG)