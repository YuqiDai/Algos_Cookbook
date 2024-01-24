# 5_Remove Nth Node from End of List
## Puzzle Description
Given the ***head*** of a linked list, remove the $n^{th}$ node from the end of the list and return its head.

## Methodology
1. Use an array to store the address of all the pointers.
2. Traverse the linked list first to get the length, then traverse again to find the $n^{th}$ one and delete it.

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
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        ListNode* array[30]={nullptr};
        ListNode* tp=head;
        int i=0,len=0,index=0;
        
        while(tp!=nullptr){
            array[i++]=tp;
            tp=tp->next;
        }

        len=i;
        index=len-n;

        if(index==0){
            head=array[1];
            return head;
        }
        else if(len-1==index){
            array[index-1]->next=nullptr;
            return head;
        }
        else{
            ListNode* left;
            ListNode* right;
            left = array[index-1];
            right = array[index+1];

            left->next=right;
            return head;
        }
    }
};
```

## Evaluation
![img](./5_Remove%20Nth%20Node%20from%20End%20of%20List.png)