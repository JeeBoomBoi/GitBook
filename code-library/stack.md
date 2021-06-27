# Stack

## Array Implementation of Stack 
```cpp
#include <iostream>
using namespace std;

struct MyStack {
    int *arr;
    int top;
    int cap;
    
    MyStack(int c) {
        cap = c;
        arr = new int[cap];
        top = -1;
    }
    
    void push(int x) {
        if (top == cap - 1) {
            cout << "Stack Overflow" << endl;
            return;
        }
        top++;
        arr[top] = x;
    }
    
    int pop() {
        if (top == -1) {
            cout << "Stack underflow" << endl;
            return -1;
        }
        int res = arr[top];
        top--;
        return res;
    }
    
    int peek() {
        if (top == -1) {
            cout << "Stack underflow" << endl;
            return -1;
        }
        return arr[top];
    }
    
    int size() {
        return (top + 1);
    }
    
    bool isEmpty() {
        return (top == -1);
    }
};

int main() {
    MyStack s(5);
    s.push(10);
    s.push(15);
    cout << s.peek() << endl;
    cout << s.pop() << endl;
    s.push(20);
    cout << s.isEmpty() << endl;
    cout << s.size() << endl;
	return 0;
}
```

## Vector Implementation of Stack
```cpp
#include <bits/stdc++.h>
using namespace std;

struct MyStack {
    vector<int> s;
    int count = 0;
    
    MyStack(int x) {
        s = vector<int>(x);
        count = 0;
    }
    
    void push(int x) {
        s.push_back(x);
        count++;
    }
    
    int pop() {
        count--;
        int e = s.back();
        s.pop_back();
        return e;
    }
    
    int peek() {
        return s.back();
    }
    
    int size() {
        return count;
    }
    
    bool isEmpty() {
        return s.empty();
    }
};

int main() {
    MyStack s(5);
    s.push(10);
    s.push(15);
    cout << s.peek() << endl;
    cout << s.pop() << endl;
    s.push(20);
    cout << s.isEmpty() << endl;
    cout << s.size() << endl;
	return 0;
}
```

## LinkedList Implementation of Stack
```cpp
#include <bits/stdc++.h>
using namespace std;

struct Node {
    int data;
    Node *next;
    
    Node(int x) {
        data = x;
        next = NULL;
    }
};

struct MyStack {
    Node *head;
    int st_size;
    
    MyStack() {
        head = NULL;
        st_size = 0;
    }
    
    void push(int x) {
        Node *temp = new Node(x);
        temp->next = head;
        head = temp;
        st_size++;
    }
    
    int pop() {
        if (head == NULL)
            return INT_MAX;
        int res = head->data;
        Node *temp = head;
        head = head->next;
        delete(temp);
        st_size--;
        return res;
    }
    
    int peek() {
        if (head == NULL) 
            return INT_MAX;
        return head->data;
    }
    
    int size() {
        return st_size;
    }
    
    bool isEmpty() {
        return (head == NULL);
    }
};

int main() {
    MyStack s;
    s.push(10);
    s.push(15);
    cout << s.peek() << endl;
    cout << s.pop() << endl;
    s.push(20);
    cout << s.isEmpty() << endl;
    cout << s.size() << endl;
	return 0;
}
```