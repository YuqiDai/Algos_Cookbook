# Insert into a Binary Search Tree
## Link
[Insert into a Binary Search Tree](https://leetcode.com/problems/insert-into-a-binary-search-tree/description/)

## Code
```cpp
class Solution {
public:
    TreeNode* insertIntoBST(TreeNode* root, int val) {
        if(root==nullptr){
            TreeNode* newNode = new TreeNode;
            newNode->left=nullptr;
            newNode->right=nullptr;
            newNode->val=val;
            return newNode;
        }

        core(root, val);

        return root;
    }

    void core(TreeNode* node, int val){
        if(node->val > val){
            if(node->left!=nullptr){
                insertIntoBST(node->left, val);
            }
            else{
                TreeNode* newNode = new TreeNode;
                newNode->left=nullptr;
                newNode->right=nullptr;
                newNode->val=val;

                node->left = newNode;
            }
        }
        else{
            if(node->right!=nullptr){
                insertIntoBST(node->right, val);
            }
            else{
                TreeNode* newNode = new TreeNode;
                newNode->left=nullptr;
                newNode->right=nullptr;
                newNode->val=val;

                node->right = newNode;
            }
        }
    }
};
```

## Evaluation
![Insert into a Binary Search Tree](./30_img.png)