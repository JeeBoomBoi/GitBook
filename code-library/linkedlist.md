# Linked List

## All operations on Linked List
```
#include<bits/stdc++.h>
using namespace std;

struct Node
{
    int data;
    Node *next;
    Node(int x)
    {
        data = x;
        next = NULL;
    }
};

void printList(Node *head)
{
    Node *curr = head;
    while(curr != NULL)
    {
        cout << curr->data << " ";
        curr = curr->next;
    }
    cout << endl;
} 

void recursiveprintList(Node *head)
{
    if (head == NULL)
    {
        cout << endl;
        return;
    }
    cout << head -> data << " ";
    recursiveprintList(head->next);
}

Node *insertBegin(Node *head, int x)
{
    Node *temp = new Node(x);
    temp->next = head;
    return temp;
}

Node *insertLast(Node *head, int x)
{
    Node *temp = new Node(x);
    Node *curr = head;
    if (head == NULL)
    {
        head = temp;
    }
    while(curr->next != NULL)
    {
        curr = curr->next;
    }
    curr->next = temp;
    return head;
}

int main()
{
    Node *head = new Node(10);
    Node *temp = new Node(20);
    Node *temp1 = new Node(30);
    head->next = temp;
    temp->next = temp1;
    head = insertBegin(head, 5);
    head = insertLast(head, 40);
    printList(head);
    // recursiveprintList(head);
    return 0;
}
```
