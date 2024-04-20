# Selection sort

## Arrays vs LinkedList

* Lists are better if you want to insert elements in the middle

| Type  | Arrays | Lists |
| ------------ |---------------| -----|
| Reading      | O(1) | O(n) |
| Insertion    | O(n) | O(1) |
| Deletion     | O(n) | O(1) |

* It’s worth mentioning that insertions and deletions are O(1) time only if you can instantly access the element to be deleted. It’s a common practice to keep track of the first and last items in a linked list, so it would take only O(1) time to delete those.
* Facebook uses a mix of both to store usernames

{% tabs %}
{% tab title="Java" %}
```java
import java.util.ArrayList;

public class SelectionSort {
    public static int findSmallest(ArrayList<Integer> arr) {
        int smallest = arr.get(0);
        int smallest_index = 0;
        for (int i = 1; i < arr.size(); i++) {
            if (arr.get(i) < smallest) {
                smallest = arr.get(i);
                smallest_index = i;
            }
        }
        return smallest_index;
    }

    public static void printArray(ArrayList<Integer> arr) {
        int n = arr.size();
        for (int i = 0; i < n; ++i)
            System.out.print(arr.get(i) + " ");
        System.out.println();
    }

    public static ArrayList<Integer> selectionSort(ArrayList<Integer> arr) {
        ArrayList<Integer> newList = new ArrayList<Integer>();
        ArrayList<Integer> copiedList = new ArrayList<>(arr);
        for (int i = 0; i < arr.size(); i++) {
            int smallest = findSmallest(copiedList);
            newList.add(copiedList.remove(smallest));
        }
        return newList;
    }

    public static void main(String[] args) {
        ArrayList<Integer> arr = new ArrayList<>();
        arr.add(5);
        arr.add(6);
        arr.add(3);
        arr.add(2);
        arr.add(10);
        printArray(selectionSort(arr));
    }
}

```
{% endtab %}

## Chapter Recap
* Your computer’s memory is like a giant set of drawers.
* When you want to store multiple elements, use an array or a linked list.
* With an array, all your elements are stored right next to each other.
* With a linked list, elements are strewn all over, and one element stores the address of the next one.
* Arrays allow fast reads.
* Linked lists allow fast inserts and deletes.
