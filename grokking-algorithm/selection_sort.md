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

---

## LinkedList implementation (Singley Linked)

```java
package Linkedlist;

public class Node {
    int data;
    // self referential structure
    Node next;  
    Node (int x) {
        data = x;
        next = null;
    }
}

public class LinkedList {
    public static void printLinkedList(Node head) {
        Node temp = head;
        while(temp != null) {
            System.out.print(temp.data + " ");
            temp = temp.next;
        }
        System.out.println();
    }

    public static Node insertBegin(Node head, int x) {
        Node temp = new Node(x);
        temp.next = head;
        return temp;
    }

    public static Node deleteHead(Node head, int x) {
        if (head == null)
            return null;
        return head.next;
    }

    public static Node deleteLastNode(Node head) {
        if (head == null || head.next == null)
            return null;
        Node temp = head;
        while (temp.next.next != null) {
            temp = temp.next;
        }
        temp.next = null;
        return head;
    }

    public static int iterativeSearch(Node head, int x) {
        int position = 1;
        Node curr = head;
        while (curr != null) {
            if (curr.data == x) {
                return position;
            }
            else {
                position++;
                curr = curr.next;
            }
        }
        return -1; 
    }

    public static int recursiveSearch(Node head, int x) {
        if (head == null) {
            return -1;
        }
        if (head.data == x) {
            return 1;
        } else {
            int res = recursiveSearch(head.next, x);
            if (res == -1) return -1;
            return res + 1;
        }
    }

    public static void main(String[] args) {
        Node head = new Node(10);
        Node temp1 = new Node(20);
        Node temp2 = new Node(30);
        head.next = temp1;
        temp1.next = temp2;
        head = insertBegin(head, 5);
        // head = deleteLastNode(head);
        System.out.println(iterativeSearch(head, 10) + " " + iterativeSearch(head, 2));
        System.out.println(recursiveSearch(head, 5) + " " + recursiveSearch(head, 2));
        printLinkedList(head);
    }
}

```
