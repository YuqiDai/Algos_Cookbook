# Remove Linked List Elements
## Puzzle Description
Given the ***head*** of a linked list and an integer ***val***, remove all the nodes of the linked list that has ***Node.val == val***, and return the new head.

## Methodology
Firstly we need to check the border(i.e Check if the first element is nullptr or not. If it is, then we need to move the head pointer backward.)   
After making sure the first element is not equal to the ***val*** given by the question, we start to check the next element by using a single loop(See the detail refer to code section).

## Code
```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* removeElements(ListNode* head, int val) {
        ListNode* tp;

        if(head==nullptr){
            return head;
        }

        while(head->val==val){
            head=head->next;
            if(head==nullptr){
                return head;
            }
        }
        tp=head;

        while(tp->next!=nullptr){
            if(tp->next->val==val){
                tp->next=tp->next->next;
            }
            else{
                tp=tp->next;
            }
        }
        return head;
    }
};
```

## Evaluation
![img](./1_Remove%20Linked%20List%20Elements.png)