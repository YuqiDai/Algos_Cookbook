# Implement Stack using Queues
## Puzzle Description
Implement a last-in-first-out (LIFO) stack using only two queues. The implemented stack should support all the functions of a normal stack (***push***, ***top***, ***pop***, and ***empty***).

Implement the ***MyStack*** class:

* ***void push(int x)*** Pushes element x to the top of the stack.
* ***int pop()*** Removes the element on the top of the stack and returns it.
* ***int top()*** Returns the element on the top of the stack.
* ***boolean empty()*** Returns true if the stack is empty, false otherwise.   

**Notes:**

You must use **only** standard operations of a queue, which means that only ***push to back***, ***peek/pop from front***, ***size*** and ***is empty*** operations are valid.
Depending on your language, the queue may not be supported natively. You may simulate a queue using a list or deque (double-ended queue) as long as you use only a queue's standard operations.


## Methodology
Easy

## Code 
```c++
class MyStack {
private:
    std::queue<int> qin;

public:
    MyStack() {}

    void push(int x) {
        qin.push(x);
    }
    
    int pop() {
        int ans=qin.back();
        int v=qin.size();
        for(int i=0;i<v-1;i++){
            int tp;
            tp=qin.front();
            qin.pop();
            qin.push(tp);
        }
        qin.pop();
        return ans;
    }
    
    int top() {
        int ans=qin.back();
        return ans;
    }
    
    bool empty() {
        if(qin.empty()) 
        return true;
        return false;
    }
};
```

## Evaluation
![img](./2_Implement%20Stack%20using%20Queues.png)