# Maximum Binary Tree
## Link
[Maximum Binary Tree](https://leetcode.com/problems/maximum-binary-tree/description/)

## Code
```cpp
class Solution {
public:
    TreeNode* constructMaximumBinaryTree(vector<int>& nums) {
        if(nums.size()==0){
            return nullptr;
        }

        return buildTree(nums, findMax(nums, 0, nums.size()-1), 0, nums.size()-1);
    }

    int findMax(vector<int> nums, int lf, int rt){
        if(lf>rt){return -1;}
        int p=lf;
        int max=nums[lf];
        lf++;

        while(!(lf>rt)){
            if(nums[lf]>max){
                max=nums[lf];
                p=lf;
            }
            lf++;
        }

        return p;
    }

    TreeNode* buildTree(vector<int>& nums, int p, int lf, int rt){
        if(lf>rt){
            return nullptr;
        }

        TreeNode* node;
        node=new(TreeNode);

        node->val=nums[p];

        node->left=buildTree(nums, findMax(nums, lf, p-1), lf, p-1);
        node->right=buildTree(nums, findMax(nums, p+1, rt), p+1, rt);

        return node;
    }
};
```

## Evaluation
![img](./22_img.PNG)