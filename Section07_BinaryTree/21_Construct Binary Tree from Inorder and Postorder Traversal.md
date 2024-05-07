# Construct Binary Tree from Inorder and Postorder Traversal
## Link
[Construct Binary Tree from Inorder and Postorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-inorder-and-postorder-traversal/description/)

## Code
```cpp
class Solution {
public:
    TreeNode* buildTree(vector<int>& inorder, vector<int>& postorder) {
        int size=inorder.size();
        if(size==0){
            return nullptr;
        }

        TreeNode* root;
        root=new(TreeNode);
        root->val=postorder[size-1];

        vector<int> inlf, inrt, polf, port;
        int i=0;
        while(inorder[i]!=root->val){
            inlf.push_back(inorder[i++]);
        }
        i++;
        while(i<size){
            inrt.push_back(inorder[i++]);
        }
        int j=0;
        for(;j<inlf.size();j++){
            polf.push_back(postorder[j]);
        }
        for(;j<size-1;j++){
            port.push_back(postorder[j]);
        }

        root->left=core(inlf, polf);
        root->right=core(inrt, port);

        return root;
    }

    TreeNode* core(vector<int> inorder, vector<int> postorder){
        int size=inorder.size();
        if(size==0){
            return nullptr;
        }

        TreeNode* child;
        child=new(TreeNode);
        child->val=postorder[size-1];

        vector<int> inlf, inrt, polf, port;
        int i=0;
        while(inorder[i]!=child->val){
            inlf.push_back(inorder[i++]);
        }
        i++;
        while(i<size){
            inrt.push_back(inorder[i++]);
        }
        int j=0;
        for(;j<inlf.size();j++){
            polf.push_back(postorder[j]);
        }
        for(;j<size-1;j++){
            port.push_back(postorder[j]);
        }

        child->left=core(inlf, polf);
        child->right=core(inrt, port);

        return  child;
    }
};
```

## Evaluation
![img](./21_img.PNG)