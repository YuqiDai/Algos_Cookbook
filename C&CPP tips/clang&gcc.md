# The differences between clang and GCC (Keep updating)
## 1. Integer overflow
These two compliers will perform different actions against integer overflow   

```cpp
//LONG_MAX and LONG_MIN are the maximun and minimum number of long type
//LONG_MAX = 2^32-1       LONG_MIN = -(2^32)

    int main(){
        int a=LONG_MAX, b=LONG_MIN;
        std::cout<<"LONG_MAX="<<a<<"__"<<"LONG_MIN="<<b;

        return 0;
    }

// Result from clang: "LONG_MAX=-1__LONG_MIN=0"
// Result from GCC:   "LONG_MAX=2147483647__LONG_MIN=-2147483648"
```