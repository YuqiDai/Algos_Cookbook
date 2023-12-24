# Special Constructor
There are two kinds of ways to define a constructor
* Method one

```c++
complex (double  r= 0, double i = 0)
{ re = r; im = i; }
```

* Method two
```c++
complex (double  r= 0, double i = 0)
: re (r), im (i) { } 
//initialize list, the code after colon is the initialization list
```

For the assignment of an object, there are two steps :   
1. variable initialization
2. variable assignment

While using the first method, we need to go through these two steps. But when we use the second method, we only go through the first step. The reason is that, on the second method, code block: 

    : re (r), im (i) {}
is actually an initialization list which is part of the initialization step. So we have already finished the variable initialization and assignment in the initialization step.    
***So, method one is slower than method two.***

[[Reference link]](https://greenhathg.github.io/2018/02/07/c++%E6%9E%84%E9%80%A0%E5%87%BD%E6%95%B0%E5%8F%A6%E4%B8%80%E7%A7%8D%E6%A0%87%E5%87%86%E5%8C%96%E5%88%9D%E5%A7%8B%E5%80%BC%E5%86%99%E6%B3%95/)