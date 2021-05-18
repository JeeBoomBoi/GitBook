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

Node *delHead(Node *head)
{
    if (head == NULL)
        return NULL;
    else
    {
        Node *temp = head->next;
        delete head;
        return temp;
    }
}

Node *delLast(Node *head)
{
    if (head == NULL)
        return NULL;
    if (head->next == NULL)
    {
        delete head;
        return NULL;
    }
    Node *curr = head;
    while(curr->next->next != NULL)
        curr = curr->next;
    delete(curr->next);
    curr->next = NULL;
    return head;
}       

Node *insertPos(Node *head, int pos, int data)
{
    Node *temp = new Node(data);
    if(pos == 1)
    {
        temp->next = head;
        return temp;
    }
    Node *curr = head;
    for (int i = 1; i <= pos-2 && curr != NULL; i++)
        curr = curr->next;
    if (curr == NULL)
        return NULL;
    temp->next = curr->next;
    curr->next = temp;
    return head;    
}

int findPos(Node *head, int x)
{
    Node *curr = head;
    int pos = 1;
    while(curr != NULL)
    {
        if (curr->data == x)
        {
            return pos;
        }
        else
        {
            pos++;
            curr = curr->next;
        }
    }
    return -1;
}

int recfindPos(Node *head, int x)
{
    if (head == NULL)
        return -1;
    if (head->data == x)
        return 1;
    else
    {
        int res = recfindPos(head->next, x);
        if (res == -1)
            return -1;
        else
            return res + 1;
    }
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
    // head = delHead(head);
    // head = delLast(head);
    head = insertPos(head, 3, 15);
    printList(head);
    cout << findPos(head, 40) << endl;
    // recursiveprintList(head);
    return 0;
}
```
