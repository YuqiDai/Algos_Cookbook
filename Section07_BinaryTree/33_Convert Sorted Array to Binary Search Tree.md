# Convert Sorted Array to Binary Search Tree
## Link
[Convert Sorted Array to Binary Search Tree](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/description/)

## Code
```cpp
class Solution {
public:
    TreeNode* sortedArrayToBST(vector<int>& nums) {
        if(nums.size()==0){
            return nullptr;
        }

        TreeNode* root = new TreeNode;
        root->val = nums[nums.size()/2];

        if(nums.size()==1){
            return root;
        }

        vector<int> numslf(nums.begin(), nums.begin()+nums.size()/2);
        corelf(numslf, root);

        if(nums.begin()+nums.size()/2+1 != nums.end()){
            vector<int> numsrt(nums.begin()+nums.size()/2+1, nums.end());
            corert(numsrt, root);
        }
        
        return root;
    }

    void corelf(vector<int>& nums, TreeNode* node){
        if(nums.size()==0){
            return ;
        }

        TreeNode* tp = new TreeNode;
        tp->val = nums[nums.size()/2];
        node->left = tp;

        if(nums.size()==1){
            return ;
        }

        vector<int> numslf(nums.begin(), nums.begin()+nums.size()/2);
        corelf(numslf, tp);

        if(nums.begin()+nums.size()/2+1 != nums.end()){
            vector<int> numsrt(nums.begin()+nums.size()/2+1, nums.end());
            corert(numsrt, tp);
        }
    }

    void corert(vector<int>& nums, TreeNode* node){
        if(nums.size()==0){
            return ;
        }

        TreeNode* tp = new TreeNode;
        tp->val = nums[nums.size()/2];
        node->right = tp;

        if(nums.size()==1){
            return ;
        }

        vector<int> numslf(nums.begin(), nums.begin()+nums.size()/2);
        corelf(numslf, tp);

        if(nums.begin()+nums.size()/2+1 != nums.end()){
            vector<int> numsrt(nums.begin()+nums.size()/2+1, nums.end());
            corert(numsrt, tp);
        }
    }
};
```

## Evaluation
![Convert Sorted Array to Binary Search Tree](./33_img.png)