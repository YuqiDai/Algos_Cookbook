# Count Complete Tree Nodes
## Link
[Count Complete Tree Nodes](https://leetcode.com/problems/count-complete-tree-nodes/description/)

## Code
```cpp
class Solution {
public:
    int countNodes(TreeNode* root) {
        TreeNode* tp=root;
        queue<TreeNode*> que;
        int sum=0;

        if(tp){
            que.push(tp);
            sum++;

            while(!que.empty()){
                int size=que.size();
                for(int i=0;i<size;i++){
                    if(que.front()->left){
                        que.push(que.front()->left);
                        sum++;
                    }
                    if(que.front()->right){
                        que.push(que.front()->right);
                        sum++;
                    }
                    que.pop();
                }
            }

        }

        return sum;
    }
};
```

## Evaluation
![img](./14_img.PNG)