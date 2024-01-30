# Reverse Linked List
## Puzzle Description
Given the **head** of a singly linked list, reverse the list, and return the *reversed list*.

## Methodology
0 extra space using. Only reverse the pointers.

## Code (Representing the second one here)
```c++
struct ListNode {
    int val;
    ListNode *next;
    ListNode() : val(0), next(nullptr) {}
    ListNode(int x) : val(x), next(nullptr) {}
    ListNode(int x, ListNode *next) : val(x), next(next) {}
};

class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        ListNode *ptp, *ptc, *tp;
        tp=head;

        ptp=tp;
        tp=tp->next;
        ptp->next=nullptr;

        while(tp->next!=nullptr){
            ptc=tp->next;
            tp->next=ptp;
            ptp=tp;
            tp=ptc;
        }
        tp->next=ptp;

        return tp;
    }
};
```

## Evaluation
![img](./Reverse%20Linked%20List.png)