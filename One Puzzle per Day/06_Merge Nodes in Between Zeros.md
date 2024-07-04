# Merge Nodes in Between Zeros
## Link
[Merge Nodes in Between Zeros](https://leetcode.com/problems/merge-nodes-in-between-zeros/description/)

## Code
```cpp
struct ListNode {
    int val;
    ListNode *next;
    ListNode() : val(0), next(nullptr) {}
    ListNode(int x) : val(x), next(nullptr) {}
    ListNode(int x, ListNode *next) : val(x), next(next) {}
};

class Solution {
public:
    ListNode* mergeNodes(ListNode* head) {
        ListNode* pre = new(ListNode);
        ListNode* tp;
        tp=pre;
        int sum=0;

        head=head->next;
        while(head!=nullptr){
            if(head->val==0){
                ListNode* node = new(ListNode);
                node->val=sum;
                tp->next=node;
                tp=tp->next;

                sum=0;
                head=head->next;
                continue;
            }

            sum+=head->val;
            head=head->next;
        }

        return pre->next;
    }
};
```

## Evaluation
![Merge Nodes in Between Zeros](./06.PNG)