# Intersection of Two Linked Lists
## Puzzle Description
Given two heads of singly linked list ***headA*** and ***headB***, please find and return the first intersection node of the two linked list. If there's no intersection node, then return ***null***.

## Methodology
1. Use hash table to store the nodes on ***headA***, then traverse the nodes on ***headB*** and compare it with the nodes in the hash table.
2. Special mathematics solution:
    * Let's say there are number of ***a*** nodes on linked list ***headA***, number of ***b*** nodes on linked list ***headB***, nunber of ***c*** represents the nubmer of  mutually held nodes 
    * If the two linked list have an intersection, then for a linked list ***headA + headB***, the number of nodes before finding the intersection node when traverse the doubled list from the first node is $a + (b - c)$.    
    For a linked list ***headB + headA***, the number of nodes before finding the intersection node when traverse the doubled list from the first node is $b + (a - c)$.

So if the two linked list have an intersection, then for two new linked list ***headA + headB*** and ***headB + headA***, there must is a same address of node when compare the two linked list one by one. If there isn't, then it means the two linked list have no intersection.

## Code
```cpp
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        ListNode *a, *b;
        a=headA;
        b=headB;

        while(a!=b){
            a=a!=nullptr?a->next:headB;
            b=b!=nullptr?b->next:headA;
        }

        return a;
    }
};
```

## Evaluation
![img](./6_Intersection%20of%20Two%20Linked%20Lists.png)