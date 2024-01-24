# Design Linked List
## Puzzle Description
Design your implementation of the linked list. You can choose to use a singly or doubly linked list.
A node in a singly linked list should have two attributes: ***val*** and ***next***.***val*** is the value of the current node, and ***next*** is a pointer/reference to the next node.
If you want to use the doubly linked list, you will need one more attribute prev to indicate the previous node in the linked list. Assume all nodes in the linked list are **0-indexed**.

## Methodology
Note: If you are new to C++ programming, remember to assign a memory space to the class instance and pointers. And delete the space using the deconstructor function.   
* At the first step, we need to design a class names MyLinkedList which is actually the combination of the structure of the nodes on the linkedlist and the functions we use to change the linkedlist.   
* Then, it's important to consider how to handle the boundarier(i.e. Empty linkedlist, list only containing one node, how to design the head node)
* At the end, if there are some bugs, you can set flags in your code to remind you where is wrong.
## Code
```c++
class MyLinkedList {
public:
    struct LinkedList{
        int val;
        LinkedList* next;

        LinkedList() : val(-1), next(nullptr) {}
    }*head;

    MyLinkedList() {
        this->head = new LinkedList();
    }
    
    int get(int index) {
        int i=0;
        LinkedList* tp=new LinkedList();
        tp=this->head;

        while(tp!=nullptr){
            if(index==i){
                return tp->val;
            }
            else{
                i++;
                tp=tp->next;
            }
        }

        return -1;
    }
    
    void addAtHead(int val) {
        LinkedList* newhead = new LinkedList();
        newhead->val = val;
        
        if(this->head->val==-1){
            this->head=newhead;
        }
        else{
            newhead->next=this->head;
            this->head=newhead;
        }
    }
    
    void addAtTail(int val) {
        LinkedList* tail = new LinkedList();
        tail->val = val;
        tail->next = nullptr;
        LinkedList* tp = this->head;

        if(this->head->val==-1){
            this->head=tail;
            return;
        }

        while(tp->next!=nullptr){
            tp=tp->next;
        }

        tp->next=tail;
    }
    
    void addAtIndex(int index, int val) {
        LinkedList* tp= this->head;
        int i=0;

        LinkedList* node=new LinkedList();
        node->val = val;

        if(index==0){
            addAtHead(val);
            return ;
        }

        do{
            if(i==index-1){
                node->next = tp->next;
                tp->next=node;
                return;
            }
            else{
                tp=tp->next;
                i++;
            }
        }while(tp!=nullptr);
    }
    
    void deleteAtIndex(int index) {
        LinkedList* tp = this->head;
        LinkedList* pref=nullptr;
        int i=0;

        if(index==0){
            this->head=this->head->next;
            return;
        }

        while(tp!=nullptr){
            if(i==index){
                pref->next=tp->next;
                return;
            }
            else{
                pref=tp;
                tp=tp->next;
                i++;
            }
        }
    }
};

/**
 * Your MyLinkedList object will be instantiated and called as such:
 * MyLinkedList* obj = new MyLinkedList();
 * int param_1 = obj->get(index);
 * obj->addAtHead(val);
 * obj->addAtTail(val);
 * obj->addAtIndex(index,val);
 * obj->deleteAtIndex(index);
 */
```

## Evaluation
![img](2_Design%20Linked%20List.png)





