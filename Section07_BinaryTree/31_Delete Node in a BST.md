# Delete Node in a BST
## Link
[Delete Node in a BST](https://leetcode.com/problems/delete-node-in-a-bst/description/)

## Code
```cpp
class Solution {
public:
    TreeNode* deleteNode(TreeNode* root, int key) {
        if(root==nullptr){
            return root;
        }
        if(root->val == key){
            if(root->left==nullptr){
                return root->right;
            }
            else if(root->right==nullptr){
                return root->left;
            }
            else{
                TreeNode* tp = root->right;
                while(tp->left!=nullptr){
                    tp=tp->left;
                }
                tp->left=root->left;
                return root->right;
            }
        }

        core(root->left, key, root);
        core(root->right, key, root);

        return root;
    }

    void core(TreeNode* node, int key, TreeNode* prev){
        if(node==nullptr) return;
        if(node->val == key){
            if(prev->left == node){
                if(node->left==nullptr){
                    prev->left = node->right;
                    return ;
                }
                else if(node->right==nullptr){
                    prev->left = node->left;
                }
                else{
                    TreeNode* tp = node->right;
                    while(tp->left!=nullptr){
                        tp=tp->left;
                    }
                    tp->left=node->left;
                    prev->left = node->right;
                }
            }
            else{
                if(node->left==nullptr){
                    prev->right = node->right;
                }
                else if(node->right==nullptr){
                    prev->right = node->left;
                }
                else{
                    TreeNode* tp = node->right;
                    while(tp->left!=nullptr){
                        tp=tp->left;
                    }
                    tp->left = node->left;
                    prev->right = node->right;
                }
            }
        }

        if(node->val > key) core(node->left, key, node);
        else core(node->right, key, node);
    }
};
```

## Evaluation
![Delete Node in a BST](./31_img.png)