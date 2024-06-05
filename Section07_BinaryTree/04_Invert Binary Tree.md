# Invert Binary Tree
## Puzzle Description
Given the `root` of a binary tree, invert the tree, and return *its root*.

## Methodology
Easy


## Code 
1. Recursive
```cpp
class Solution {
public:
    TreeNode* invertTree(TreeNode* root) {
        TreeNode* tp=root;
        if(tp){
            invertunit(tp->left);
            invertunit(tp->right);
            TreeNode* mid;
            mid=tp->left;
            tp->left=tp->right;
            tp->right=mid;
        }

        return root;
    }

    void invertunit(TreeNode* tp){
        if(tp){
            invertunit(tp->left);
            invertunit(tp->right);
            TreeNode* mid;
            mid=tp->left;
            tp->left=tp->right;
            tp->right=mid;
        }
    }
};
```

2. Iterative
```cpp
class Solution {
public:
    TreeNode* invertTree(TreeNode* root) {
        TreeNode* tp=root;
        stack<TreeNode*> st;

        if(tp){
            st.push(tp);
        }

        while(!st.empty()){
            tp=st.top();
            st.pop();

            TreeNode* mid;
            mid=tp->left;
            tp->left=tp->right;
            tp->right=mid;

            if(tp->right){
                st.push(tp->right);
            }
            if(tp->left){
                st.push(tp->left);
            }
        }

        return root;
    }
};
```


## Evaluation
1. Recursive    

![recursive](./04_recursive.png)

2. Iterative    

![iterative](./04_iterative.png)