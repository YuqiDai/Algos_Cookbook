# Implement Queue using Stacks
## Puzzle Description
Implement a first in first out (FIFO) queue using only two stacks. The implemented queue should support all the functions of a normal queue (***push***, ***peek***, ***pop***, and ***empty***).

Implement the ***MyQueue*** class:

* ***void push(int x)*** Pushes element x to the back of the queue.
* ***int pop()*** Removes the element from the front of the queue and returns it.
* ***int peek()*** Returns the element at the front of the queue.
* ***boolean empty()*** Returns ***true*** if the queue is empty, ***false*** otherwise.

**Notes:**

* You must use **only** standard operations of a stack, which means only ***push to top***, ***peek/pop from top***, ***size***, and ***is empty*** operations are valid.
* Depending on your language, the stack may not be supported natively. You may simulate a stack using a list or deque (double-ended queue) as long as you use only a stack's standard operations.

## Methodology
Easy

## Code 
```c++
class MyQueue {
private:
    std::stack<int, int> stk1,stk2;
public:
    MyQueue() {}
    
    void push(int x) {
        stk1.push(x);
    }
    
    int pop() {
        while(!stk1.empty()){
            stk2.push(stk1.top());
            stk1.pop();
        }
        stk2.pop();
        while(!stk2.empty()){
            stk1.push(stk2.top());
            stk2.pop();
        }
    }
    
    int peek() {
        while(!stk1.empty()){
            stk2.push(stk1.top());
            stk1.pop();
        }
        int ans=stk2.top();
        while(!stk2.empty()){
            stk1.push(stk2.top());
            stk2.pop();
        }
        return ans;
    }
    
    bool empty() {
        if(stk1.empty()){
            return true;
        }
        else{
            return false;
        }
    }
};

```

## Evaluation
![img](./1_Implement%20Queue%20using%20Stacks.png)