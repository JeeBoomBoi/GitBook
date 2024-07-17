## LinkedList implementation (Singley Linked)

```java
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
