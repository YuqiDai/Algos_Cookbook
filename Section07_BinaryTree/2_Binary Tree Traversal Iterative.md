# Binary Tree Traversal Iterative
## Puzzle Description
Given the root of a binary tree, return the `preorder`/`postorder`/`inorder` traversal of its nodes' values.

## Methodology
Easy

## Code 
```cpp
//Definition for a binary tree node.
struct TreeNode {
    int val;
    TreeNode *left;
    TreeNode *right;
    TreeNode() : val(0), left(nullptr), right(nullptr) {}
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
    TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
};

class Solution {
public:
    vector<int> inorderTraversal(TreeNode* root) {
        vector<int> ans;
        stack<TreeNode*> st;
        TreeNode* tp=root;

        if(tp!=nullptr){
            st.push(tp);
        }

        while(!st.empty()){
            tp=st.top();
            
            if(tp!=nullptr){
                st.pop();
                if(tp->right){
                    st.push(tp->right);
                }
                st.push(tp);
                st.push(nullptr);
                if(tp->left){
                    st.push(tp->left);
                }
            }
            else{
                st.pop();
                tp=st.top();
                st.pop();
                ans.push_back(tp->val);
            }
        }

        return ans;
    }

    vector<int> preorderTraversal(TreeNode* root) {
        vector<int> ans;
        stack<TreeNode*> st;
        TreeNode* tp=root;

        if(tp!=nullptr){
            st.push(tp);
        }

        while(!st.empty()){
            tp=st.top();
            st.pop();

            ans.push_back(tp->val);
            
            if(tp->right){
                st.push(tp->right);
            }
            if(tp->left){
                st.push(tp->left);
            }
        }

        return ans;
    }

    vector<int> postorderTraversal(TreeNode* root) {
        vector<int> ans;
        stack<TreeNode*> st;
        TreeNode* tp=root;

        if(tp){
            st.push(tp);
        }

        while(!st.empty()){
            tp=st.top();
            

            if(tp!=nullptr){
                st.pop();
                st.push(tp);
                st.push(nullptr);
                if(tp->right){
                    st.push(tp->right);
                }
                if(tp->left){
                    st.push(tp->left);
                }
            }
            else{
                st.pop();
                tp=st.top();
                st.pop();
                ans.push_back(tp->val);
            }
        }
        return ans;
    }
};
```

## Evaluation
![Binary Tree Traversal Iterative](./2_Binary%20Tree%20Traversal%20Iterative.png)