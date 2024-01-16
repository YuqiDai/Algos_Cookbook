# Reverse Linked List
## Puzzle Description
Given the **head** of a singly linked list, reverse the list, and return the *reversed list*.

## Methodology
1. Recursion: Initialize another head called newhead, using recursion to find the end node of the waiting-for-reversing list, then start filling the newlist.
2. Normal way: Initialize an array ***int array[5001]***, traverse the existing list and copy the ***val*** to the array. Then move the ***val*** back to the list.

## Code (Representing the second one here)
```c++
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
    ListNode* reverseList(ListNode* head) {
        ListNode* tp;
        tp=head;
        int array[5001];
        int num=0;

        while(tp!=nullptr){
            array[num]=tp->val;
            num++;
            tp=tp->next;
        }

        tp=head;
        for(num;num>0;num--){
            tp->val=array[num-1];
            tp=tp->next;
        }

        return head;
    }
};
```
## Evaluation
![img](./3_Reverse%20Linked%20List.png)