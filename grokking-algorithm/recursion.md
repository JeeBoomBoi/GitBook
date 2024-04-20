# Recursion

Loops may achieve a performance gain for your program. Recursion may achieve a performance gain for your programmer. Choose which is more important in your situation!

* Every recursive function has two parts: the base case and the recursive case.

```java
class Solution{
    static long factorial(int N){
        // code here
        if (N <= 1) {
            return 1;
        }
        return N * factorial(N - 1);
    }
}
```

## Chapter Recap
* Recursion is when a function calls itself.
* Every recursive function has two cases: the base case and the recursive case.
* A stack has two operations: push and pop.
* All function calls go onto the call stack.
* The call stack can get very large, which takes up a lot of memory.
