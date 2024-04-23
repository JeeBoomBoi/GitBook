# Quicksort

* Uses Divide and Conquer strategy, used Euclid's algorithm as an example with respect to dividing land into equal parts

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

## Quicksort implementation
```java
package snips;

import java.util.ArrayList;
import java.util.Scanner;

public class QuickSort {
    public static ArrayList<Integer> lessArray(ArrayList<Integer> arr, int pivot) {
        ArrayList<Integer> less = new ArrayList<>();
        for (int i = 0; i < arr.size(); i++) {
            if (pivot > arr.get(i)) {
                less.add(arr.get(i));
            }
        }
        return less;
    }

    public static ArrayList<Integer> greaterArray(ArrayList<Integer> arr, int pivot) {
        ArrayList<Integer> greater = new ArrayList<>();
        for (int i = 0; i < arr.size(); i++) {
            if (pivot < arr.get(i)) {
                greater.add(arr.get(i));
            }
        }
        return greater;
    }

    public static ArrayList<Integer> quickSort(ArrayList<Integer> arr) {
        if (arr.size() < 2) {
            return arr;
        } else {
            int pivot = arr.get(0);
            ArrayList<Integer> less = lessArray(arr, pivot);
            ArrayList<Integer> greater = greaterArray(arr, pivot);
            less = quickSort(less);
            less.add(pivot);
            less.addAll(quickSort(greater));
            return less;
        }
    }

    public static void printArray(ArrayList<Integer> arr) {
        int n = arr.size();
        for (int i = 0; i < n; ++i)
            System.out.print(arr.get(i) + " ");
        System.out.println();
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
        sc.close();
        printArray(quickSort(list));
    }
}
```

## Chapter recap

* D&C works by breaking a problem down into smaller and smaller pieces. If you’re using D&C on a list, the base case is probably an empty array or an array with one element.

* If you’re implementing quicksort, choose a random element as the pivot. The average run time of quicksort is O(n log n)!

* Given two algorithms with the same big O running time, one can be consistently faster than the other. That’s why quicksort is faster than merge sort.

* The constant almost never matters for simple search versus binary search because O(log n) is so much faster than O(n) when your list gets big.
