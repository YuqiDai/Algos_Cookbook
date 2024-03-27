# Sum of Nodes with Even-Valued Grandparent
## Puzzle Description
Given the `root` of a binary tree, return *the sum of values of nodes with an* ***even-valued grandparent***. If there are no nodes with an **even-valued grandparent**, return `0`.

A **grandparent** of a node is the parent of its parent if it exists.

## Methodology
1. Use preorder traversal to traverse the whole tree nodes.
2. Conduct the action on every nodes.
3. Extra question: Why we use recursive here rather than iterative.

## Code
```cpp
class Solution {
public:
    int sumEvenGrandparent(TreeNode* root) {
        int sum=0;
        if(root){
            unit(root, sum);
        }
        return sum;
    }

    void unit(TreeNode* node, int& sum){
        if(node){
            if(node->val%2==0)
            {
                if(node->left){
                    if(node->left->left){
                        sum+=node->left->left->val;
                    }
                    if(node->left->right){
                        sum+=node->left->right->val;
                    }
                }
                if(node->right){
                    if(node->right->left){
                        sum+=node->right->left->val;
                    }
                    if(node->right->right){
                        sum+=node->right->right->val;
                    }
                }
            }
            unit(node->left,sum);
            unit(node->right, sum);
```

## Evaluation
![img](./Sum%20of%20Nodes%20with%20Even-Valued%20Grandparent.png)
