# Merge Two Binary Trees
## Link
[Merge Two Binary Trees](https://leetcode.com/problems/search-in-a-binary-search-tree/description/)

## Code
```cpp
class Solution {
public:
    TreeNode* mergeTrees(TreeNode* root1, TreeNode* root2) {
        if(root1==nullptr&&root2==nullptr){
            return nullptr;
        }
        if(root1==nullptr){
            return root2;
        }
        if(root2==nullptr){
            return root1;
        }

        core(root1, root2);
        return root1;
    }

    void core(TreeNode* node1, TreeNode* node2){
        node1->val+=node2->val;

        if(node1->left!=nullptr&&node2->left!=nullptr){
            core(node1->left, node2->left);
        }
        if(node1->right!=nullptr&&node2->right!=nullptr){
            core(node1->right, node2->right);
        }

        if(node1->left==nullptr&&node2->left!=nullptr){
            node1->left=node2->left;
        }
        if(node1->right==nullptr&&node2->right!=nullptr){
            node1->right=node2->right;
        }
    }
};
```

## Evaluation
![img](./23_img.PNG)