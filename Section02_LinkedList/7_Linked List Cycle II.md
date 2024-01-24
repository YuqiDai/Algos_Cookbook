# Linked List Cycle II
## Description
Given the ***head*** of a linked list, return the node where the cycle begins. If there is no cycle, return ***null***.   
Do not modify the linked list.

## Methodology
There are two options:
1. Use hash table (i.e. In c++ you can use unordered_set) to store the node on the linked list, then check whether the node at the next pointer is repeated. If is, return the node and finish; If not, continue.
2. Use mathematical tricks to handle this issue. Refer to this link ([Solution](https://leetcode.com/problems/linked-list-cycle-ii/solutions/1701128/c-java-python-slow-and-fast-image-explanation-beginner-friendly/))

## Code
For option one:
```c++
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
    ListNode *detectCycle(ListNode *head) {
        std::unordered_set<ListNode*> array;
        ListNode* tp=head;

        if(head==nullptr){
            std::cout<<"no cycle";
            return NULL;
        }

        while(tp!=nullptr){
            if(array.find(tp)==array.end()){
                array.insert(tp);
                tp=tp->next;
            }
            else{
                return tp;
            }
            
        }

        return NULL;
    }
};
```

For option two:
```c++
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
    ListNode *detectCycle(ListNode *head) {
        ListNode* fast=head;
        ListNode* slow=head;

        while(true){
            if(fast==nullptr||fast->next==nullptr){return NULL;}
            fast=fast->next->next;
            slow=slow->next;
            if(fast==slow){
                break;
            }
        }
        fast = head;
        while(fast!=slow){
            fast=fast->next;
            slow=slow->next;
        }
        return fast;
    }
};
```

## Evaluation
* For option one:
    ![img1](./7_Linked%20List%20Cycle%20II%20img1.png)    
     
* For option two:
    ![img2](./7_Linked%20List%20Cycle%20II%20img2.png)