# Populating Next Right Pointers in Each Node
## 1. Link
[Populating Next Right Pointers in Each Node](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/description/)

## 2. Code
```cpp
class Solution {
public:
    Node* connect(Node* root) {
        Node* tp=root;
        queue<Node*> que;
        que.push(tp);

        if(tp){
            while(!que.empty()){
                int size=que.size();
                for(int i=0;i<size;i++){
                    Node* intp=que.front();

                    if(que.front()->left){
                        que.push(que.front()->left);
                    }
                    if(que.front()->right){
                        que.push(que.front()->right);
                    }

                    que.pop();
                    if(i==size-1){
                        continue;
                    }
                    
                    intp->next=que.front();
                }
            }
        }
        return root;
    }
};
```

## 3. Evaluation
![img](./10_img.png)