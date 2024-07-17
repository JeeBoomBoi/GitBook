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

## Recursive Practice
```java
package snips;

import java.util.ArrayList;
import java.util.Scanner;

public class RecursivePractice {
    public static int sum(ArrayList<Integer> arr) {
        if (arr.size() == 0) {
            return 0;
        } else {
            int x = arr.remove(0);
            return x + sum(arr);
        }
    } 

    public static int count(ArrayList<Integer> arr) {
        if (arr.size() == 0) {
            return 0;
        } else {
            arr.remove(0);
            return 1 + count(arr);
        }
    }

    public static int max(ArrayList<Integer> arr) {
        if (arr.size() == 0) {
            return Integer.MIN_VALUE;
        } else {
            int x = arr.remove(0);
            int y = max(arr);
            return y > x ? y : x;
        }
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.println("Enter size of the array");
        int size = sc.nextInt();
        ArrayList<Integer> list = new ArrayList<>();
        for (int i = 0; i < size; i++) {
            int e = sc.nextInt();
            list.add(e);
        }
        // System.out.println("Sum of elements" + " " + sum(list));
        // System.out.println("Count of elements" + " " + count(list));
        System.out.println("Max of elements" + " " + max(list));

        sc.close();
    }
}
```

## Chapter Recap
* Recursion is when a function calls itself.
* Every recursive function has two cases: the base case and the recursive case.
* A stack has two operations: push and pop.
* All function calls go onto the call stack.
* The call stack can get very large, which takes up a lot of memory.
