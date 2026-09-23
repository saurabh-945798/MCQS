# C++ Debugging — Data Structures & Algorithms

## Question 1

### Difficulty
Easy

### Bug Type
Array-Based Stack Push Wrong Top Index

### Problem
This program implements an array-based integer stack. `push()` adds an element, `pop()` removes and prints the top element, and `size()` prints how many elements are currently stored. The push routine updates the top index before writing into the array, so the very first slot is never used and data lands one position too high.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

class Stack {
public:
    int data[10] = {0};
    int top = 0;

    void push(int x) {
        top++;
        if (top <= 10) data[top] = x;
    }

    void pop() {
        if (top == 0) {
            cout << "Underflow\n";
            return;
        }
        cout << "Popped: " << data[--top] << "\n";
    }

    void sizeStack() const {
        cout << "Size: " << top << "\n";
    }
};

int main() {
    Stack s;
    int cmd, x;
    while (cin >> cmd) {
        if (cmd == 1) {
            cin >> x;
            s.push(x);
        } else if (cmd == 2) {
            s.pop();
        } else if (cmd == 3) {
            s.sizeStack();
        }
    }
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
3
```
the expected output is:
```text
Size: 0
```

For:
```text
1 10 2 2
```
the expected output is:
```text
Popped: 10
Underflow
```

For:
```text
1 10 1 20 3 2 2
```
the expected output is:
```text
Size: 2
Popped: 20
Popped: 10
```

---

## Question 2

### Difficulty
Easy

### Bug Type
Stack Pop Underflow Check Wrong

### Problem
This program uses an array-based stack where `top` counts the number of stored elements. `pop()` should print the removed element, and print `Underflow` whenever the stack is empty. The underflow check inside `pop()` uses the wrong boundary, so it prints `Underflow` even when the last element is still stored.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

class Stack {
public:
    int data[10] = {0};
    int top = 0;

    void push(int x) {
        data[top++] = x;
    }

    void pop() {
        top--;
        if (top <= 0) {
            cout << "Underflow\n";
            top++;
            return;
        }
        cout << "Popped: " << data[top] << "\n";
    }
};

int main() {
    Stack s;
    int cmd, x;
    while (cin >> cmd) {
        if (cmd == 1) {
            cin >> x;
            s.push(x);
        } else if (cmd == 2) {
            s.pop();
        }
    }
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
2
```
the expected output is:
```text
Underflow
```

For:
```text
1 42 2
```
the expected output is:
```text
Popped: 42
```

For:
```text
1 5 1 9 2 2
```
the expected output is:
```text
Popped: 9
Popped: 5
```

---

## Question 3

### Difficulty
Easy

### Bug Type
Queue Front/Rear Index Error

### Problem
This program implements a simple array-based queue with `enqueue()`, `dequeue()` and `display()`. The `rear` index tracks the next free cell. `dequeue()` must remove and print the element at the front of the queue, but it reads the cell at the `rear` index instead of the `front` index, so every dequeue reports the wrong value.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

class Queue {
public:
    int data[8] = {0};
    int front = 0, rear = 0;

    void enqueue(int x) {
        data[rear++] = x;
    }

    void dequeue() {
        if (front == rear) {
            cout << "Queue empty\n";
            return;
        }
        cout << "Removed: " << data[rear] << "\n";
        front++;
    }

    void display() const {
        if (front == rear) {
            cout << "Empty\n";
            return;
        }
        cout << "Queue:";
        for (int i = front; i < rear; i++) cout << " " << data[i];
        cout << "\n";
    }
};

int main() {
    Queue q;
    int cmd, x;
    while (cin >> cmd) {
        if (cmd == 1) {
            cin >> x;
            q.enqueue(x);
        } else if (cmd == 2) {
            q.dequeue();
        } else if (cmd == 3) {
            q.display();
        }
    }
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
2
```
the expected output is:
```text
Queue empty
```

For:
```text
1 10 1 20 2 3
```
the expected output is:
```text
Removed: 10
Queue: 20
```

For:
```text
1 30 2
```
the expected output is:
```text
Removed: 30
```

---

## Question 4

### Difficulty
Easy

### Bug Type
Linked List Count Misses Last Node

### Problem
A singly linked list is built by pushing values at the head. `countNodes()` is supposed to return the number of nodes currently in the list. Its while-loop advances until the penultimate node, so the final node in the list is never counted.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;
};

void pushFront(Node*& head, int x) {
    head = new Node{x, head};
}

int countNodes(Node* head) {
    int c = 0;
    Node* p = head;
    while (p && p->next) {
        c++;
        p = p->next;
    }
    return c;
}

int main() {
    int n, x;
    cin >> n;
    Node* head = nullptr;
    for (int i = 0; i < n; i++) {
        cin >> x;
        pushFront(head, x);
    }
    cout << "Count: " << countNodes(head) << "\n";
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
0
```
the expected output is:
```text
Count: 0
```

For:
```text
1 42
```
the expected output is:
```text
Count: 1
```

For:
```text
4 1 2 3 4
```
the expected output is:
```text
Count: 4
```

---

## Question 5

### Difficulty
Easy

### Bug Type
Recursive Sum Base Case Wrong

### Problem
`sum()` is a recursive function that adds together the numbers in an integer array. The recursion should return 0 for an empty array. Instead its base case returns `a[0]`, so for every non-empty array the first element gets counted a second time and the total is too large by exactly `a[0]`.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int sum(int a[], int n) {
    if (n == 0) return a[0];
    return a[n - 1] + sum(a, n - 1);
}

int main() {
    int n;
    cin >> n;
    int a[100] = {0};
    for (int i = 0; i < n; i++) cin >> a[i];
    cout << "Sum: " << sum(a, n) << "\n";
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
0
```
the expected output is:
```text
Sum: 0
```

For:
```text
3 10 20 30
```
the expected output is:
```text
Sum: 60
```

For:
```text
1 5
```
the expected output is:
```text
Sum: 5
```

---

## Question 6

### Difficulty
Easy

### Bug Type
unordered_map Frequency Update (`=` instead of `++`)

### Problem
This program reads a lowercase word and counts how many times each letter appears using an `unordered_map<char, int>`. The frequency update line assigns a constant instead of incrementing, so a character that appears many times is always recorded with count 1.

### Buggy Code

```cpp
#include <iostream>
#include <unordered_map>
#include <string>
using namespace std;

int main() {
    string s;
    cin >> s;
    unordered_map<char, int> freq;
    for (char c : s) {
        freq[c] = 1;
    }
    for (char c = 'a'; c <= 'z'; c++) {
        if (freq.count(c)) cout << c << ":" << freq[c] << " ";
    }
    cout << "\n";
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
abc
```
the expected output is:
```text
a:1 b:1 c:1
```

For:
```text
aab
```
the expected output is:
```text
a:2 b:1
```

For:
```text
banana
```
the expected output is:
```text
a:3 b:1 n:2
```

## Question 7

### Difficulty
Easy

### Bug Type
Stack Peek Off-by-One

### Problem
This program implements an array-based stack where `top` counts the number of stored elements. `peek()` must print the value sitting on top of the stack. It prints `data[top]` instead of `data[top - 1]`, so it inspects the empty slot just above the top element and always reports 0 whenever at least one value exists.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

class Stack {
public:
    int data[10] = {0};
    int top = 0;

    void push(int x) {
        data[top++] = x;
    }

    void peek() {
        if (top == 0) {
            cout << "Empty\n";
            return;
        }
        cout << "Top: " << data[top] << "\n";
    }
};

int main() {
    Stack s;
    int cmd, x;
    while (cin >> cmd) {
        if (cmd == 1) {
            cin >> x;
            s.push(x);
        } else if (cmd == 2) {
            s.peek();
        }
    }
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
2
```
the expected output is:
```text
Empty
```

For:
```text
1 42 2
```
the expected output is:
```text
Top: 42
```

For:
```text
1 3 1 5 2
```
the expected output is:
```text
Top: 5
```

---

## Question 8

### Difficulty
Easy

### Bug Type
Queue Rear Update Wrong

### Problem
This program implements a plain array-based queue using `front` and `rear` indices. `enqueue()` writes the new value into the array but never advances the `rear` index, so every inserted value overwrites the same cell. Because `front` and `rear` stay equal, `dequeue()` always reports the queue as empty.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

class Queue {
public:
    int data[8] = {0};
    int front = 0, rear = 0;

    void enqueue(int x) {
        data[rear] = x;
    }

    void dequeue() {
        if (front == rear) {
            cout << "Queue empty\n";
            return;
        }
        cout << "Removed: " << data[front] << "\n";
        front++;
    }
};

int main() {
    Queue q;
    int cmd, x;
    while (cin >> cmd) {
        if (cmd == 1) {
            cin >> x;
            q.enqueue(x);
        } else if (cmd == 2) {
            q.dequeue();
        }
    }
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
2
```
the expected output is:
```text
Queue empty
```

For:
```text
1 5 2
```
the expected output is:
```text
Removed: 5
```

For:
```text
1 5 1 9 2
```
the expected output is:
```text
Removed: 5
```

---

## Question 9

### Difficulty
Medium

### Bug Type
Circular Queue Wrap-Around Condition

### Problem
This program implements a circular queue of capacity 5 with a `count` field and `head`/`tail` indices. `enqueue()` advances `tail` with a modulo expression so the buffer can wrap. The wrap-around formula uses `(tail + 1) % 4` instead of `(tail + 1) % 5`, so one slot is skipped, the heap of stored values drifts, and the fifth insertion overwrites the first value.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

class CircularQueue {
public:
    int data[5] = {0};
    int head = 0, tail = 0, count = 0;

    void enqueue(int x) {
        if (count == 5) {
            cout << "Queue full\n";
            return;
        }
        data[tail] = x;
        count++;
        tail = (tail + 1) % 4;
    }

    void dequeue() {
        if (count == 0) {
            cout << "Queue empty\n";
            return;
        }
        cout << "Removed: " << data[head] << "\n";
        head = (head + 1) % 5;
        count--;
    }

    void display() {
        cout << "Queue:";
        for (int i = 0; i < count; i++) cout << " " << data[(head + i) % 5];
        cout << "\n";
    }
};

int main() {
    CircularQueue q;
    int cmd, x;
    while (cin >> cmd) {
        if (cmd == 1) {
            cin >> x;
            q.enqueue(x);
        } else if (cmd == 2) {
            q.dequeue();
        } else if (cmd == 3) {
            q.display();
        }
    }
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
1 7 2
```
the expected output is:
```text
Removed: 7
```

For:
```text
1 10 1 20 1 30 1 40 1 50 3
```
the expected output is:
```text
Queue: 10 20 30 40 50
```

---

## Question 10

### Difficulty
Medium

### Bug Type
Linked List Append Doesn't Link New Node

### Problem
`append()` should add a new node at the end of a singly linked list. It walks to the tail, creates a new node, and assigns it to a local pointer. The last existing node never gets linked to the new node, so only the very first appended value remains reachable.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;
};

void append(Node*& head, int x) {
    if (!head) {
        head = new Node{x, nullptr};
        return;
    }
    Node* p = head;
    while (p) p = p->next;
    p = new Node{x, nullptr};
}

void display(Node* head) {
    cout << "List:";
    for (Node* p = head; p; p = p->next) cout << " " << p->data;
    cout << "\n";
}

int main() {
    Node* head = nullptr;
    int n, x;
    cin >> n;
    for (int i = 0; i < n; i++) {
        cin >> x;
        append(head, x);
    }
    display(head);
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
1 9
```
the expected output is:
```text
List: 9
```

For:
```text
3 1 2 3
```
the expected output is:
```text
List: 1 2 3
```

For:
```text
2 7 8
```
the expected output is:
```text
List: 7 8
```

---

## Question 11

### Difficulty
Medium

### Bug Type
Linked List Delete Missing Prev Update

### Problem
A linked list is built with `pushFront()` and `removeNode()` deletes the first node that holds a given value. Removing the head works, but for any node inside the list the previous node's link is never used: the function deletes the node that follows the match instead, leaving the matched node in place.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;
};

void pushFront(Node*& head, int x) {
    head = new Node{x, head};
}

void removeNode(Node*& head, int x) {
    Node* p = head;
    while (p && p->data != x) p = p->next;
    if (!p) return;
    if (p == head) {
        head = p->next;
        delete p;
        return;
    }
    Node* doomed = p->next;
    p->next = doomed->next;
    delete doomed;
}

void display(Node* head) {
    cout << "List:";
    for (Node* p = head; p; p = p->next) cout << " " << p->data;
    cout << "\n";
}

int main() {
    Node* head = nullptr;
    int n, x, target;
    cin >> n;
    for (int i = 0; i < n; i++) {
        cin >> x;
        pushFront(head, x);
    }
    cin >> target;
    removeNode(head, target);
    display(head);
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
3 1 2 3
3
```
the expected output is:
```text
List: 2 1
```

For:
```text
5 5 10 15 20 25
15
```
the expected output is:
```text
List: 25 20 10 5
```

---

## Question 12

### Difficulty
Medium

### Bug Type
Reverse Linked List Wrong Next Update

### Problem
`reverse()` must reverse a singly linked list in place so the traversal direction flips. The loop saves the successor and rolls `prev` forward, but it never points the current node at its predecessor — it only reassigns the node to its own unchanged successor. At the end `head` points to the original tail, and walking it yields a single node.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;
};

void pushFront(Node*& head, int x) {
    head = new Node{x, head};
}

void reverse(Node*& head) {
    Node* prev = nullptr;
    Node* p = head;
    while (p) {
        Node* next = p->next;
        prev = p;
        p->next = next;
        p = p->next;
    }
    head = prev;
}

void display(Node* head) {
    cout << "Reversed:";
    for (Node* p = head; p; p = p->next) cout << " " << p->data;
    cout << "\n";
}

int main() {
    Node* head = nullptr;
    int n, x;
    cin >> n;
    for (int i = 0; i < n; i++) {
        cin >> x;
        pushFront(head, x);
    }
    reverse(head);
    display(head);
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
1 7
```
the expected output is:
```text
Reversed: 7
```

For:
```text
3 1 2 3
```
the expected output is:
```text
Reversed: 1 2 3
```

---

## Question 13

### Difficulty
Medium

### Bug Type
BST Insert Doesn't Attach Node

### Problem
A binary search tree is pre-seeded with a root of 10. `insert()` should add integers into the proper places and the program prints an in-order traversal of the tree. The `insert()` function takes the root pointer by value, so when it reaches an empty spot the freshly allocated node is discarded and nothing is ever attached to the tree.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

struct TreeNode {
    int data;
    TreeNode* left;
    TreeNode* right;
    TreeNode(int x) : data(x), left(nullptr), right(nullptr) {}
};

void insert(TreeNode* r, int x) {
    if (!r) {
        r = new TreeNode(x);
        return;
    }
    if (x < r->data) insert(r->left, x);
    else insert(r->right, x);
}

void inorder(TreeNode* r) {
    if (!r) return;
    inorder(r->left);
    cout << r->data << " ";
    inorder(r->right);
}

int main() {
    TreeNode* root = new TreeNode(10);
    int k, x;
    cin >> k;
    for (int i = 0; i < k; i++) {
        cin >> x;
        insert(root, x);
    }
    cout << "Inorder: ";
    inorder(root);
    cout << "\n";
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
0
```
the expected output is:
```text
Inorder: 10
```

For:
```text
3 5 15 3
```
the expected output is:
```text
Inorder: 3 5 10 15
```

---

## Question 14

### Difficulty
Medium

### Bug Type
BST Search Wrong Comparison Direction

### Problem
A binary search tree is built correctly by inserting integers. `search()` must report whether a given key exists by following the correct subtree at every node. When the key is smaller than the current node's value the recursion wrongly descends into the right subtree instead of the left one.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

struct TreeNode {
    int data;
    TreeNode* left;
    TreeNode* right;
    TreeNode(int x) : data(x), left(nullptr), right(nullptr) {}
};

void insert(TreeNode*& r, int x) {
    if (!r) {
        r = new TreeNode(x);
        return;
    }
    if (x < r->data) insert(r->left, x);
    else insert(r->right, x);
}

bool search(TreeNode* r, int x) {
    if (!r) return false;
    if (r->data == x) return true;
    if (x < r->data) return search(r->right, x);
    return search(r->left, x);
}

int main() {
    int n, x, key;
    cin >> n;
    TreeNode* root = nullptr;
    for (int i = 0; i < n; i++) {
        cin >> x;
        insert(root, x);
    }
    cin >> key;
    cout << (search(root, key) ? "Found\n" : "Not found\n");
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
3 5 3 9
5
```
the expected output is:
```text
Found
```

For:
```text
3 5 3 9
9
```
the expected output is:
```text
Found
```

For:
```text
3 5 3 9
3
```
the expected output is:
```text
Found
```

---

## Question 15

### Difficulty
Medium

### Bug Type
Tree Height Wrong Max Comparison

### Problem
`height()` computes the height of a binary tree where an empty subtree has height 0. It should take the larger of the two child heights and add one. Instead it adds the left and right heights together, which over-inflates the height for every node that owns both a left and a right subtree.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

struct TreeNode {
    int data;
    TreeNode* left;
    TreeNode* right;
    TreeNode(int x) : data(x), left(nullptr), right(nullptr) {}
};

void insert(TreeNode*& r, int x) {
    if (!r) {
        r = new TreeNode(x);
        return;
    }
    if (x < r->data) insert(r->left, x);
    else insert(r->right, x);
}

int height(TreeNode* r) {
    if (!r) return 0;
    int leftH = height(r->left);
    int rightH = height(r->right);
    return leftH + rightH + 1;
}

int main() {
    int n, x;
    cin >> n;
    TreeNode* root = nullptr;
    for (int i = 0; i < n; i++) {
        cin >> x;
        insert(root, x);
    }
    cout << "Height: " << height(root) << "\n";
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
1 42
```
the expected output is:
```text
Height: 1
```

For:
```text
5 3 1 5 7 4
```
the expected output is:
```text
Height: 3
```

---

## Question 16

### Difficulty
Medium

### Bug Type
In-Order Traversal Output Order Wrong

### Problem
`inorder()` is supposed to print a binary tree using an in-order traversal: left subtree, then the node, then the right subtree. The print statement runs before both recursive calls, so the node is emitted first and the traversal is actually a pre-order traversal.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

struct TreeNode {
    int data;
    TreeNode* left;
    TreeNode* right;
    TreeNode(int x) : data(x), left(nullptr), right(nullptr) {}
};

void insert(TreeNode*& r, int x) {
    if (!r) {
        r = new TreeNode(x);
        return;
    }
    if (x < r->data) insert(r->left, x);
    else insert(r->right, x);
}

void inorder(TreeNode* r) {
    if (!r) return;
    cout << r->data << " ";
    inorder(r->left);
    inorder(r->right);
}

int main() {
    int n, x;
    cin >> n;
    TreeNode* root = nullptr;
    for (int i = 0; i < n; i++) {
        cin >> x;
        insert(root, x);
    }
    cout << "Inorder: ";
    inorder(root);
    cout << "\n";
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
1 5
```
the expected output is:
```text
Inorder: 5
```

For:
```text
3 4 2 6
```
the expected output is:
```text
Inorder: 2 4 6
```

---

## Question 17

### Difficulty
Medium

### Bug Type
Stack Reverse Using Wrong Pop Order

### Problem
This program reverses a sequence using a stack: every value is pushed, then the values are popped into a result array. The index used when copying each popped value is wrong — the top of the stack is written into `rev[n - 1 - i]` instead of `rev[i]` — so the printed result comes out in the original, unreversed order.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
#include <stack>
using namespace std;

int main() {
    int n;
    cin >> n;
    vector<int> a(n);
    for (int i = 0; i < n; i++) cin >> a[i];

    stack<int> st;
    for (int i = 0; i < n; i++) st.push(a[i]);

    vector<int> rev(n);
    for (int i = 0; i < n; i++) {
        rev[n - 1 - i] = st.top();
        st.pop();
    }

    for (int i = 0; i < n; i++) cout << rev[i] << " ";
    cout << "\n";
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
1 7
```
the expected output is:
```text
7
```

For:
```text
4 1 2 3 4
```
the expected output is:
```text
4 3 2 1
```

---

## Question 18

### Difficulty
Medium

### Bug Type
Level-Order (BFS) Traversal Wrong Push Order

### Problem
`levelOrder()` walks a binary tree level by level using a queue, printing each node as it is taken out. When a node has children, the code pushes the right child to the queue before the left child, so each level is visited in mirrored order.

### Buggy Code

```cpp
#include <iostream>
#include <queue>
using namespace std;

struct TreeNode {
    int data;
    TreeNode* left;
    TreeNode* right;
    TreeNode(int x) : data(x), left(nullptr), right(nullptr) {}
};

void insert(TreeNode*& r, int x) {
    if (!r) {
        r = new TreeNode(x);
        return;
    }
    if (x < r->data) insert(r->left, x);
    else insert(r->right, x);
}

void levelOrder(TreeNode* root) {
    queue<TreeNode*> q;
    q.push(root);
    while (!q.empty()) {
        TreeNode* p = q.front();
        q.pop();
        cout << p->data << " ";
        if (p->left) q.push(p->right);
        if (p->right) q.push(p->left);
    }
}

int main() {
    int n, x;
    cin >> n;
    TreeNode* root = nullptr;
    for (int i = 0; i < n; i++) {
        cin >> x;
        insert(root, x);
    }
    cout << "BFS: ";
    levelOrder(root);
    cout << "\n";
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
1 5
```
the expected output is:
```text
BFS: 5
```

For:
```text
3 4 2 6
```
the expected output is:
```text
BFS: 4 2 6
```

---

## Question 19

### Difficulty
Medium

### Bug Type
unordered_map Charcount getOrDefault Misuse

### Problem
This program counts letter frequencies with an `unordered_map` and a small helper `getCount()` that behaves like a getOrDefault lookup: it returns the existing count or 0 when the key is missing. The update line stores the looked-up value as if it were the new total. Because it never adds one, every repeated occurrence simply re-sets the counter to its old value.

### Buggy Code

```cpp
#include <iostream>
#include <algorithm>
#include <unordered_map>
#include <string>
using namespace std;

int getCount(const unordered_map<char, int>& m, char c) {
    auto it = m.find(c);
    return (it == m.end()) ? 0 : it->second;
}

int main() {
    string s;
    cin >> s;
    unordered_map<char, int> freq;
    for (char c : s) {
        freq[c] = max(getCount(freq, c), 1);
    }
    for (char c = 'a'; c <= 'z'; c++) {
        if (freq.count(c)) cout << c << ":" << freq[c] << " ";
    }
    cout << "\n";
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
xyz
```
the expected output is:
```text
x:1 y:1 z:1
```

For:
```text
aabbc
```
the expected output is:
```text
a:2 b:2 c:1
```

## Question 20

### Difficulty
Hard

### Bug Type
Linked List Cycle Detection Slow/Fast Wrong Update

### Problem
This program builds a linked list and optionally closes a cycle by pointing the tail at the second node. `hasCycle()` must detect the cycle using slow and fast pointers. Both pointers advance one step per iteration, so the fast pointer never gains ground and any acyclic list of two or more nodes is falsely reported as cyclic.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;
};

void pushFront(Node*& head, int x) {
    head = new Node{x, head};
}

bool hasCycle(Node* head) {
    Node* slow = head;
    Node* fast = head;
    while (fast && fast->next) {
        slow = slow->next;
        fast = fast->next;
        if (slow == fast) return true;
    }
    return false;
}

int main() {
    int n, x, makeCycle;
    cin >> n;
    Node* head = nullptr;
    for (int i = 0; i < n; i++) {
        cin >> x;
        pushFront(head, x);
    }
    cin >> makeCycle;
    if (makeCycle) {
        Node* p = head;
        while (p->next) p = p->next;
        p->next = head->next;
    }
    cout << (hasCycle(head) ? "Cycle: true\n" : "Cycle: false\n");
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
1 42 0
```
the expected output is:
```text
Cycle: false
```

For:
```text
3 1 2 3 0
```
the expected output is:
```text
Cycle: false
```

For:
```text
3 1 2 3 1
```
the expected output is:
```text
Cycle: true
```

---

## Question 21

### Difficulty
Hard

### Bug Type
Linked List Middle Slow/Fast Wrong Initialization

### Problem
`middle()` finds the middle value of a singly linked list using the slow/fast pointer trick. The two pointers are started from the same node and both advance one step per loop iteration, so the pointers stay together and the function walks to the very end of the list and reports the last node as the middle.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;
};

void pushFront(Node*& head, int x) {
    head = new Node{x, head};
}

int middle(Node* head) {
    Node* slow = head;
    Node* fast = head;
    while (fast && fast->next) {
        slow = slow->next;
        fast = fast->next;
    }
    return slow->data;
}

int main() {
    int n, x;
    cin >> n;
    Node* head = nullptr;
    for (int i = 0; i < n; i++) {
        cin >> x;
        pushFront(head, x);
    }
    cout << "Middle: " << middle(head) << "\n";
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
1 7
```
the expected output is:
```text
Middle: 7
```

For:
```text
5 1 2 3 4 5
```
the expected output is:
```text
Middle: 3
```

---

## Question 22

### Difficulty
Hard

### Bug Type
Mirror Tree Swaps Only the Root

### Problem
`mirror()` is meant to transform a binary tree into its mirror image so that an in-order traversal prints the values in reverse. The function swaps the root's children but never recurses into the subtrees, so every sub-tree below the root keeps its original children and only the top two branches flip.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

struct TreeNode {
    int data;
    TreeNode* left;
    TreeNode* right;
    TreeNode(int x) : data(x), left(nullptr), right(nullptr) {}
};

void insert(TreeNode*& r, int x) {
    if (!r) {
        r = new TreeNode(x);
        return;
    }
    if (x < r->data) insert(r->left, x);
    else insert(r->right, x);
}

void mirror(TreeNode* r) {
    if (!r) return;
    TreeNode* t = r->left;
    r->left = r->right;
    r->right = t;
}

void inorder(TreeNode* r) {
    if (!r) return;
    inorder(r->left);
    cout << r->data << " ";
    inorder(r->right);
}

int main() {
    int n, x;
    cin >> n;
    TreeNode* root = nullptr;
    for (int i = 0; i < n; i++) {
        cin >> x;
        insert(root, x);
    }
    mirror(root);
    cout << "Inorder: ";
    inorder(root);
    cout << "\n";
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
1 9
```
the expected output is:
```text
Inorder: 9
```

For:
```text
7 4 2 1 3 6 5 7
```
the expected output is:
```text
Inorder: 7 6 5 4 3 2 1
```

---

## Question 23

### Difficulty
Hard

### Bug Type
Count Leaf Nodes Recursion Wrong

### Problem
`countLeaves()` counts the leaf nodes of a binary tree — nodes that have no children at all. Every internal (non-leaf) node adds an extra 1 on top of the leaves found in its subtrees, so the result is inflated by the number of internal nodes.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

struct TreeNode {
    int data;
    TreeNode* left;
    TreeNode* right;
    TreeNode(int x) : data(x), left(nullptr), right(nullptr) {}
};

void insert(TreeNode*& r, int x) {
    if (!r) {
        r = new TreeNode(x);
        return;
    }
    if (x < r->data) insert(r->left, x);
    else insert(r->right, x);
}

int countLeaves(TreeNode* r) {
    if (!r) return 0;
    if (!r->left && !r->right) return 1;
    return 1 + countLeaves(r->left) + countLeaves(r->right);
}

int main() {
    int n, x;
    cin >> n;
    TreeNode* root = nullptr;
    for (int i = 0; i < n; i++) {
        cin >> x;
        insert(root, x);
    }
    cout << "Leaves: " << countLeaves(root) << "\n";
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
1 42
```
the expected output is:
```text
Leaves: 1
```

For:
```text
7 4 2 1 3 6 5 7
```
the expected output is:
```text
Leaves: 4
```

---

## Question 24

### Difficulty
Hard

### Bug Type
Tree Diameter Recursive Accumulation Wrong

### Problem
`diameter()` reports the number of nodes on the longest path inside a binary tree. It uses a helper that also returns each subtree's height. The helper returns the sum of the two child heights instead of the greater height plus one, so heights balloon and the diameter is over-counted.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

struct TreeNode {
    int data;
    TreeNode* left;
    TreeNode* right;
    TreeNode(int x) : data(x), left(nullptr), right(nullptr) {}
};

void insert(TreeNode*& r, int x) {
    if (!r) {
        r = new TreeNode(x);
        return;
    }
    if (x < r->data) insert(r->left, x);
    else insert(r->right, x);
}

int height(TreeNode* r, int& best) {
    if (!r) return 0;
    int l = height(r->left, best);
    int rr = height(r->right, best);
    if (l + rr + 1 > best) best = l + rr + 1;
    return l + rr + 1;
}

int diameter(TreeNode* root) {
    int best = 0;
    height(root, best);
    return best;
}

int main() {
    int n, x;
    cin >> n;
    TreeNode* root = nullptr;
    for (int i = 0; i < n; i++) {
        cin >> x;
        insert(root, x);
    }
    cout << "Diameter: " << diameter(root) << "\n";
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
1 42
```
the expected output is:
```text
Diameter: 1
```

For:
```text
7 4 2 1 3 6 5 7
```
the expected output is:
```text
Diameter: 5
```

---

## Question 25

### Difficulty
Hard

### Bug Type
Recursive GCD Wrong Base Case

### Problem
`gcd()` computes the greatest common divisor of two integers using Euclid's recursion. A base case has been added that treats two equal numbers as having GCD 1, which is only valid for the pair (1, 1). Any other equal pair, like (12, 12), is answered incorrectly.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int gcd(int a, int b) {
    if (a == b) return 1;
    if (b == 0) return a;
    return gcd(b, a % b);
}

int main() {
    int a, b;
    cin >> a >> b;
    cout << "GCD: " << gcd(a, b) << "\n";
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
12 18
```
the expected output is:
```text
GCD: 6
```

For:
```text
12 12
```
the expected output is:
```text
GCD: 12
```

For:
```text
35 10
```
the expected output is:
```text
GCD: 5
```

## Question 26

### Difficulty
Hard

### Bug Type
Recursive Fibonacci Wrong Base (0 and 1)

### Problem
`fib()` computes the n-th Fibonacci number recursively. The two base cases have their return values swapped: `fib(0)` returns 1 and `fib(1)` returns 0. Inputs from n = 3 onward therefore drift from the correct Fibonacci sequence.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int fib(int n) {
    if (n == 0) return 1;
    if (n == 1) return 0;
    return fib(n - 1) + fib(n - 2);
}

int main() {
    int n;
    cin >> n;
    cout << "Fib(" << n << "): " << fib(n) << "\n";
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
2
```
the expected output is:
```text
Fib(2): 1
```

For:
```text
6
```
the expected output is:
```text
Fib(6): 8
```

For:
```text
10
```
the expected output is:
```text
Fib(10): 55
```

---

## Question 27

### Difficulty
Hard

### Bug Type
Sum of Digits Recursion Wrong Extraction

### Problem
`sumDigits()` must return the sum of the decimal digits of a non-negative integer. The recursive step extracts the wrong part of the number: it adds `n / 10` to each level of recursion instead of `n % 10`, so every leading digit is counted many times.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

int sumDigits(int n) {
    if (n == 0) return 0;
    return n / 10 + sumDigits(n / 10);
}

int main() {
    int n;
    cin >> n;
    cout << "Sum: " << sumDigits(n) << "\n";
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
0
```
the expected output is:
```text
Sum: 0
```

For:
```text
123
```
the expected output is:
```text
Sum: 6
```

For:
```text
2024
```
the expected output is:
```text
Sum: 8
```

---

## Question 28

### Difficulty
Hard

### Bug Type
Balanced Parentheses Stack Mismatch

### Problem
`isBalanced()` decides whether a string made of `()`, `[]` and `{}` is properly balanced, using a stack of opening brackets. The closing-bracket matching conditions are wrong: `]` is paired with `{` and `}` is paired with `[`. Some mismatched strings are accepted and some valid strings are rejected.

### Buggy Code

```cpp
#include <iostream>
#include <stack>
#include <string>
using namespace std;

bool isBalanced(const string& s) {
    stack<char> st;
    for (char c : s) {
        if (c == '(' || c == '[' || c == '{') {
            st.push(c);
        } else {
            if (st.empty()) return false;
            char top = st.top();
            if ((c == ')' && top == '(') ||
                (c == ']' && top == '{') ||
                (c == '}' && top == '[')) {
                st.pop();
            } else {
                return false;
            }
        }
    }
    return st.empty();
}

int main() {
    string s;
    cin >> s;
    cout << (isBalanced(s) ? "Balanced\n" : "Not balanced\n");
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
()
```
the expected output is:
```text
Balanced
```

For:
```text
[}
```
the expected output is:
```text
Not balanced
```

For:
```text
([])
```
the expected output is:
```text
Balanced
```

---

## Question 29

### Difficulty
Hard

### Bug Type
Next Greater Element Stack Bug

### Problem
For each element of an array this program prints the next element to its right that is strictly greater, or -1 if no such element exists. The monotonic-stack cleanup pops while the top is smaller but keeps equal values, so a following equal element is wrongly reported where a strictly greater one is required.

### Buggy Code

```cpp
#include <iostream>
#include <vector>
#include <stack>
using namespace std;

int main() {
    int n;
    cin >> n;
    vector<int> a(n);
    for (int i = 0; i < n; i++) cin >> a[i];

    vector<int> res(n, -1);
    stack<int> st;
    for (int i = n - 1; i >= 0; i--) {
        while (!st.empty() && st.top() < a[i]) st.pop();
        if (!st.empty()) res[i] = st.top();
        st.push(a[i]);
    }

    for (int i = 0; i < n; i++) cout << res[i] << " ";
    cout << "\n";
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
3 4 5 2
```
the expected output is:
```text
5 -1 -1
```

For:
```text
3 2 2 3
```
the expected output is:
```text
3 3 -1
```

---

## Question 30

### Difficulty
Hard

### Bug Type
Two Related Bugs (stack boundary + loop)

### Problem
A fixed-capacity stack (5 slots) is filled from standard input and then displayed from top to bottom. Two tightly related bugs ruin it: the overflow check rejects a push one slot too early, and the display loop runs from index `top` down to index 1, printing one stale zero cell and never printing the element stored at index 0.

### Buggy Code

```cpp
#include <iostream>
using namespace std;

class Stack {
public:
    int data[5] = {0};
    int top = 0;

    void push(int x) {
        if (top + 2 == 5) {
            cout << "Stack overflow\n";
            return;
        }
        data[top++] = x;
    }

    void display() {
        if (top == 0) {
            cout << "Stack: (empty)\n";
            return;
        }
        cout << "Stack:";
        for (int i = top; i >= 1; i--) cout << " " << data[i];
        cout << "\n";
    }
};

int main() {
    Stack s;
    int n, x;
    cin >> n;
    for (int i = 0; i < n; i++) {
        cin >> x;
        s.push(x);
    }
    s.display();
    return 0;
}
```

### Task
Find the bug and correct the code.

### Expected Behavior

For:
```text
0
```
the expected output is:
```text
Stack: (empty)
```

For:
```text
4 10 20 30 40
```
the expected output is:
```text
Stack: 40 30 20 10
```

For:
```text
3 7 8 9
```
the expected output is:
```text
Stack: 9 8 7
```

# Solutions

## Solution 1

### Bug
In `push()` the stack writes to `data[top]` only after incrementing `top`, so the first push lands in slot 1 and slot 0 is permanently left as the zero-filled cell that `pop()` later reads.

### Explanation
With the buggy code, `push(10)` performs `top++; data[top] = x`, so the value is stored at index 1 while `pop()` reads `data[--top]`, i.e. `data[0]`, which was never written. For input `1 10 2 2` the expected output is `Popped: 10` then `Underflow`, but the buggy program prints `Popped: 0` then `Underflow`. Similarly for `1 10 1 20 3 2 2` it prints `Size: 2`, `Popped: 20`, `Popped: 0` instead of `Popped: 20`, `Popped: 10`. The fix is to store the value first and move `top` afterwards.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

class Stack {
public:
    int data[10] = {0};
    int top = 0;

    void push(int x) {
        if (top >= 10) {
            cout << "Stack full\n";
            return;
        }
        data[top++] = x;
    }

    void pop() {
        if (top == 0) {
            cout << "Underflow\n";
            return;
        }
        cout << "Popped: " << data[--top] << "\n";
    }

    void sizeStack() const {
        cout << "Size: " << top << "\n";
    }
};

int main() {
    Stack s;
    int cmd, x;
    while (cin >> cmd) {
        if (cmd == 1) {
            cin >> x;
            s.push(x);
        } else if (cmd == 2) {
            s.pop();
        } else if (cmd == 3) {
            s.sizeStack();
        }
    }
    return 0;
}
```

## Solution 2

### Bug
`pop()` decrements `top` before its underflow test and then treats `top <= 0` as empty, so popping the genuinely last element (which leaves `top` equal to 0) is misreported as an underflow.

### Explanation
With one element stored, `top` is 1. The buggy `pop()` does `top--` (now 0), then `top <= 0` is true and it prints `Underflow` instead of removing `data[0]`. For input `1 42 2` the expected output is `Popped: 42`, but the buggy program prints `Underflow`. For `1 5 1 9 2 2` it prints `Popped: 9` followed by `Underflow` instead of `Popped: 5`. Check for emptiness before changing `top`.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

class Stack {
public:
    int data[10] = {0};
    int top = 0;

    void push(int x) {
        data[top++] = x;
    }

    void pop() {
        if (top == 0) {
            cout << "Underflow\n";
            return;
        }
        cout << "Popped: " << data[--top] << "\n";
    }
};

int main() {
    Stack s;
    int cmd, x;
    while (cin >> cmd) {
        if (cmd == 1) {
            cin >> x;
            s.push(x);
        } else if (cmd == 2) {
            s.pop();
        }
    }
    return 0;
}
```

## Solution 3

### Bug
`dequeue()` prints `data[rear]`, the next free cell, instead of `data[front]`, the actual front element.

### Explanation
After enqueuing 10 and 20, `front` is 0 and `rear` is 2. The buggy `dequeue()` prints `data[2]`, an untouched zero-filled cell, so `1 10 1 20 2 3` prints `Removed: 0` and `Queue: 20` instead of `Removed: 10` and `Queue: 20`. Input `1 30 2` prints `Removed: 0` instead of `Removed: 30`. Read from the front index.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

class Queue {
public:
    int data[8] = {0};
    int front = 0, rear = 0;

    void enqueue(int x) {
        data[rear++] = x;
    }

    void dequeue() {
        if (front == rear) {
            cout << "Queue empty\n";
            return;
        }
        cout << "Removed: " << data[front] << "\n";
        front++;
    }

    void display() const {
        if (front == rear) {
            cout << "Empty\n";
            return;
        }
        cout << "Queue:";
        for (int i = front; i < rear; i++) cout << " " << data[i];
        cout << "\n";
    }
};

int main() {
    Queue q;
    int cmd, x;
    while (cin >> cmd) {
        if (cmd == 1) {
            cin >> x;
            q.enqueue(x);
        } else if (cmd == 2) {
            q.dequeue();
        } else if (cmd == 3) {
            q.display();
        }
    }
    return 0;
}
```

## Solution 4

### Bug
The counting loop stops when `p->next` is null, so it never counts the final node of the list.

### Explanation
For `1 42` the loop condition `p && p->next` is false immediately because the single node's `next` is null, so `countNodes()` returns 0 instead of 1. For `4 1 2 3 4` it returns 3 instead of 4. Walk until `p` itself becomes null and count every visited node.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;
};

void pushFront(Node*& head, int x) {
    head = new Node{x, head};
}

int countNodes(Node* head) {
    int c = 0;
    Node* p = head;
    while (p) {
        c++;
        p = p->next;
    }
    return c;
}

int main() {
    int n, x;
    cin >> n;
    Node* head = nullptr;
    for (int i = 0; i < n; i++) {
        cin >> x;
        pushFront(head, x);
    }
    cout << "Count: " << countNodes(head) << "\n";
    return 0;
}
```

## Solution 5

### Bug
The empty-array base case returns `a[0]` instead of 0, so the first element is added a second time for every non-empty array.

### Explanation
For `3 10 20 30`, recursion unfolds as `30 + 20 + 10 + a[0]` = 70 instead of 60. Input `1 5` gives 5 + 5 = 10 instead of 5. Return 0 when `n` reaches 0.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int sum(int a[], int n) {
    if (n == 0) return 0;
    return a[n - 1] + sum(a, n - 1);
}

int main() {
    int n;
    cin >> n;
    int a[100] = {0};
    for (int i = 0; i < n; i++) cin >> a[i];
    cout << "Sum: " << sum(a, n) << "\n";
    return 0;
}
```

## Solution 6

### Bug
The frequency update overwrites each counter with the constant 1 instead of incrementing it.

### Explanation
For `aab` the map contains `a:1` and `b:1` after both `a`s are processed, so the output is `a:1 b:1` instead of `a:2 b:1`. Input `banana` prints `a:1 b:1 n:1` instead of `a:3 b:1 n:2`. Replace the assignment with an increment so repeats accumulate.

### Corrected Code

```cpp
#include <iostream>
#include <unordered_map>
#include <string>
using namespace std;

int main() {
    string s;
    cin >> s;
    unordered_map<char, int> freq;
    for (char c : s) {
        freq[c]++;
    }
    for (char c = 'a'; c <= 'z'; c++) {
        if (freq.count(c)) cout << c << ":" << freq[c] << " ";
    }
    cout << "\n";
    return 0;
}
```

## Solution 7

### Bug
`peek()` reads `data[top]` instead of `data[top - 1]`, inspecting the empty slot just above the stored elements.

### Explanation
After `push(42)`, `top` is 1 and the value sits at `data[0]`. The buggy `peek()` prints `data[1]`, which is still zero from the array's zero-initialisation, so input `1 42 2` prints `Top: 0` instead of `Top: 42`. Next-greater input `1 3 1 5 2` prints `Top: 0` instead of `Top: 5`. Index one below `top`.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

class Stack {
public:
    int data[10] = {0};
    int top = 0;

    void push(int x) {
        data[top++] = x;
    }

    void peek() {
        if (top == 0) {
            cout << "Empty\n";
            return;
        }
        cout << "Top: " << data[top - 1] << "\n";
    }
};

int main() {
    Stack s;
    int cmd, x;
    while (cin >> cmd) {
        if (cmd == 1) {
            cin >> x;
            s.push(x);
        } else if (cmd == 2) {
            s.peek();
        }
    }
    return 0;
}
```

## Solution 8

### Bug
`enqueue()` stores the value but never advances the `rear` index, so each new value overwrites `data[0]` and the queue looks permanently empty.

### Explanation
After `enqueue(5)`, `rear` is still 0 and `front` equals `rear`, so `dequeue()` prints `Queue empty` instead of `Removed: 5`. The same happens for `1 5 1 9 2`, which should print `Removed: 5`. Advance `rear` when storing the value.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

class Queue {
public:
    int data[8] = {0};
    int front = 0, rear = 0;

    void enqueue(int x) {
        data[rear++] = x;
    }

    void dequeue() {
        if (front == rear) {
            cout << "Queue empty\n";
            return;
        }
        cout << "Removed: " << data[front] << "\n";
        front++;
    }
};

int main() {
    Queue q;
    int cmd, x;
    while (cin >> cmd) {
        if (cmd == 1) {
            cin >> x;
            q.enqueue(x);
        } else if (cmd == 2) {
            q.dequeue();
        }
    }
    return 0;
}
```

## Solution 9

### Bug
The wrap-around formula is `(tail + 1) % 4` instead of `(tail + 1) % 5`, so slot 4 is never used and the fifth stored value collides with the value in slot 0.

### Explanation
Enqueuing 10, 20, 30, 40 fills slots 0–3 and `tail` wraps back to 0; the fifth enqueue, 50, lands in slot 0 and overwrites 10. The display then prints `Queue: 50 20 30 40 0` instead of `Queue: 10 20 30 40 50`. Mod out by the full capacity: `(tail + 1) % 5`.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

class CircularQueue {
public:
    int data[5] = {0};
    int head = 0, tail = 0, count = 0;

    void enqueue(int x) {
        if (count == 5) {
            cout << "Queue full\n";
            return;
        }
        data[tail] = x;
        count++;
        tail = (tail + 1) % 5;
    }

    void dequeue() {
        if (count == 0) {
            cout << "Queue empty\n";
            return;
        }
        cout << "Removed: " << data[head] << "\n";
        head = (head + 1) % 5;
        count--;
    }

    void display() {
        cout << "Queue:";
        for (int i = 0; i < count; i++) cout << " " << data[(head + i) % 5];
        cout << "\n";
    }
};

int main() {
    CircularQueue q;
    int cmd, x;
    while (cin >> cmd) {
        if (cmd == 1) {
            cin >> x;
            q.enqueue(x);
        } else if (cmd == 2) {
            q.dequeue();
        } else if (cmd == 3) {
            q.display();
        }
    }
    return 0;
}
```

## Solution 10

### Bug
`append()` walks off the end of the list and assigns the new node to the local pointer `p`, never linking it to the current tail.

### Explanation
For `3 1 2 3`, the first value 1 becomes the head; appending 2 and 3 creates orphaned nodes that are never reached from the head, so the output is `List: 1` instead of `List: 1 2 3`. Stop the walk at the last node (`p->next`) and attach the new node through it.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;
};

void append(Node*& head, int x) {
    if (!head) {
        head = new Node{x, nullptr};
        return;
    }
    Node* p = head;
    while (p->next) p = p->next;
    p->next = new Node{x, nullptr};
}

void display(Node* head) {
    cout << "List:";
    for (Node* p = head; p; p = p->next) cout << " " << p->data;
    cout << "\n";
}

int main() {
    Node* head = nullptr;
    int n, x;
    cin >> n;
    for (int i = 0; i < n; i++) {
        cin >> x;
        append(head, x);
    }
    display(head);
    return 0;
}
```

## Solution 11

### Bug
For an interior node the function never uses the previous node's link: it deletes the node that follows the match instead of the matched node.

### Explanation
For `5 5 10 15 20 25` the list is `25 20 15 10 5`. Removing 15 should give `List: 25 20 10 5`, but the buggy code deletes node 10 (the one after the match), leaving `List: 25 20 15 5`. Track the predecessor and link it to `p->next` before deleting `p`.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;
};

void pushFront(Node*& head, int x) {
    head = new Node{x, head};
}

void removeNode(Node*& head, int x) {
    Node* p = head;
    Node* prev = nullptr;
    while (p && p->data != x) {
        prev = p;
        p = p->next;
    }
    if (!p) return;
    if (prev == nullptr) {
        head = p->next;
    } else {
        prev->next = p->next;
    }
    delete p;
}

void display(Node* head) {
    cout << "List:";
    for (Node* p = head; p; p = p->next) cout << " " << p->data;
    cout << "\n";
}

int main() {
    Node* head = nullptr;
    int n, x, target;
    cin >> n;
    for (int i = 0; i < n; i++) {
        cin >> x;
        pushFront(head, x);
    }
    cin >> target;
    removeNode(head, target);
    display(head);
    return 0;
}
```

## Solution 12

### Bug
The loop never performs the relinking step `p->next = prev`; it only saves the successor and rolls `prev` forward, so at the end `head` points at the original tail node.

### Explanation
For `3 1 2 3` the list is `3 2 1`. The loop leaves every link untouched and finishes with `prev` equal to the last node (value 1), so the display prints `Reversed: 1` instead of `Reversed: 1 2 3`. Point the current node at `prev`, then walk forward using the saved successor.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;
};

void pushFront(Node*& head, int x) {
    head = new Node{x, head};
}

void reverse(Node*& head) {
    Node* prev = nullptr;
    Node* p = head;
    while (p) {
        Node* next = p->next;
        p->next = prev;
        prev = p;
        p = next;
    }
    head = prev;
}

void display(Node* head) {
    cout << "Reversed:";
    for (Node* p = head; p; p = p->next) cout << " " << p->data;
    cout << "\n";
}

int main() {
    Node* head = nullptr;
    int n, x;
    cin >> n;
    for (int i = 0; i < n; i++) {
        cin >> x;
        pushFront(head, x);
    }
    reverse(head);
    display(head);
    return 0;
}
```

## Solution 13

### Bug
`insert(TreeNode* r, int x)` takes the root by value, so assigning `r = new TreeNode(x)` modifies only a local copy and no node is ever linked into the tree.

### Explanation
Inserting 5, 15 and 3 into the pre-seeded tree produces no new node at all, so the in-order traversal prints only the root: `Inorder: 10` instead of `Inorder: 3 5 10 15`. Pass the pointer by reference so the assignment propagates to the caller's pointer.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

struct TreeNode {
    int data;
    TreeNode* left;
    TreeNode* right;
    TreeNode(int x) : data(x), left(nullptr), right(nullptr) {}
};

void insert(TreeNode*& r, int x) {
    if (!r) {
        r = new TreeNode(x);
        return;
    }
    if (x < r->data) insert(r->left, x);
    else insert(r->right, x);
}

void inorder(TreeNode* r) {
    if (!r) return;
    inorder(r->left);
    cout << r->data << " ";
    inorder(r->right);
}

int main() {
    TreeNode* root = new TreeNode(10);
    int k, x;
    cin >> k;
    for (int i = 0; i < k; i++) {
        cin >> x;
        insert(root, x);
    }
    cout << "Inorder: ";
    inorder(root);
    cout << "\n";
    return 0;
}
```

## Solution 14

### Bug
`search()` descends into the right subtree when the key is smaller than the current value, and into the left subtree otherwise — the comparison branches are swapped.

### Explanation
In the tree `5(3, 9)`, searching for 9 should take the right child and print `Found`. The buggy code takes the left child, reaches a null pointer, and prints `Not found`. Searching for 3 returns `Not found` as well. Use the left branch for `x < r->data` and the right branch otherwise.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

struct TreeNode {
    int data;
    TreeNode* left;
    TreeNode* right;
    TreeNode(int x) : data(x), left(nullptr), right(nullptr) {}
};

void insert(TreeNode*& r, int x) {
    if (!r) {
        r = new TreeNode(x);
        return;
    }
    if (x < r->data) insert(r->left, x);
    else insert(r->right, x);
}

bool search(TreeNode* r, int x) {
    if (!r) return false;
    if (r->data == x) return true;
    if (x < r->data) return search(r->left, x);
    return search(r->right, x);
}

int main() {
    int n, x, key;
    cin >> n;
    TreeNode* root = nullptr;
    for (int i = 0; i < n; i++) {
        cin >> x;
        insert(root, x);
    }
    cin >> key;
    cout << (search(root, key) ? "Found\n" : "Not found\n");
    return 0;
}
```

## Solution 15

### Bug
`height()` returns `leftH + rightH + 1`; the two child heights are summed instead of selecting the larger one.

### Explanation
For the tree `3(1, 5(4, 7))` the true height is 3. The buggy calculation returns `1 + 3 + 1 = 5` because nodes with two children accumulate both subtrees. A single-node tree still passes (`Height: 1`), which masks the error until a balanced-ish tree is tested. Keep the bigger branch only.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

struct TreeNode {
    int data;
    TreeNode* left;
    TreeNode* right;
    TreeNode(int x) : data(x), left(nullptr), right(nullptr) {}
};

void insert(TreeNode*& r, int x) {
    if (!r) {
        r = new TreeNode(x);
        return;
    }
    if (x < r->data) insert(r->left, x);
    else insert(r->right, x);
}

int height(TreeNode* r) {
    if (!r) return 0;
    int leftH = height(r->left);
    int rightH = height(r->right);
    return (leftH > rightH ? leftH : rightH) + 1;
}

int main() {
    int n, x;
    cin >> n;
    TreeNode* root = nullptr;
    for (int i = 0; i < n; i++) {
        cin >> x;
        insert(root, x);
    }
    cout << "Height: " << height(root) << "\n";
    return 0;
}
```

## Solution 16

### Bug
`inorder()` prints the node before visiting its children, which turns the traversal into a pre-order one.

### Explanation
For the tree `4(2, 6)` the correct in-order output is `2 4 6`, but the buggy function prints `4 2 6` because the root is emitted first. Move the print between the two recursive calls.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

struct TreeNode {
    int data;
    TreeNode* left;
    TreeNode* right;
    TreeNode(int x) : data(x), left(nullptr), right(nullptr) {}
};

void insert(TreeNode*& r, int x) {
    if (!r) {
        r = new TreeNode(x);
        return;
    }
    if (x < r->data) insert(r->left, x);
    else insert(r->right, x);
}

void inorder(TreeNode* r) {
    if (!r) return;
    inorder(r->left);
    cout << r->data << " ";
    inorder(r->right);
}

int main() {
    int n, x;
    cin >> n;
    TreeNode* root = nullptr;
    for (int i = 0; i < n; i++) {
        cin >> x;
        insert(root, x);
    }
    cout << "Inorder: ";
    inorder(root);
    cout << "\n";
    return 0;
}
```

## Solution 17

### Bug
Popped values are written into `rev[n - 1 - i]` instead of `rev[i]`, so the stack-popping order is applied at the wrong position and the result array keeps the original order.

### Explanation
Pushing 1, 2, 3, 4 and popping gives 4, 3, 2, 1. The buggy code stores those values into `rev[3]`, `rev[2]`, `rev[1]`, `rev[0]`, so the printed row is `1 2 3 4` instead of `4 3 2 1`. Write each popped value into `rev[i]` directly.

### Corrected Code

```cpp
#include <iostream>
#include <vector>
#include <stack>
using namespace std;

int main() {
    int n;
    cin >> n;
    vector<int> a(n);
    for (int i = 0; i < n; i++) cin >> a[i];

    stack<int> st;
    for (int i = 0; i < n; i++) st.push(a[i]);

    vector<int> rev(n);
    for (int i = 0; i < n; i++) {
        rev[i] = st.top();
        st.pop();
    }

    for (int i = 0; i < n; i++) cout << rev[i] << " ";
    cout << "\n";
    return 0;
}
```

## Solution 18

### Bug
`levelOrder()` pushes the right child to the queue before the left child whenever either exists.

### Explanation
For the tree `4(2, 6)`, the root is printed, then the queue receives 6 before 2, so the output is `BFS: 4 6 2` instead of `BFS: 4 2 6`. Push the left child first, then the right child.

### Corrected Code

```cpp
#include <iostream>
#include <queue>
using namespace std;

struct TreeNode {
    int data;
    TreeNode* left;
    TreeNode* right;
    TreeNode(int x) : data(x), left(nullptr), right(nullptr) {}
};

void insert(TreeNode*& r, int x) {
    if (!r) {
        r = new TreeNode(x);
        return;
    }
    if (x < r->data) insert(r->left, x);
    else insert(r->right, x);
}

void levelOrder(TreeNode* root) {
    queue<TreeNode*> q;
    q.push(root);
    while (!q.empty()) {
        TreeNode* p = q.front();
        q.pop();
        cout << p->data << " ";
        if (p->left) q.push(p->left);
        if (p->right) q.push(p->right);
    }
}

int main() {
    int n, x;
    cin >> n;
    TreeNode* root = nullptr;
    for (int i = 0; i < n; i++) {
        cin >> x;
        insert(root, x);
    }
    cout << "BFS: ";
    levelOrder(root);
    cout << "\n";
    return 0;
}
```

## Solution 19

### Bug
The update `freq[c] = max(getCount(freq, c), 1)` stores the looked-up value (or its floor of 1) instead of adding one to it, so counters never grow past 1.

### Explanation
For `aabbc` the first `a` sets 1, the second `a` looks up 1 and stores `max(1, 1) = 1`, so the output is `a:1 b:1 c:1` instead of `a:2 b:2 c:1`. Replace the assignment with an increment of the looked-up value.

### Corrected Code

```cpp
#include <iostream>
#include <algorithm>
#include <unordered_map>
#include <string>
using namespace std;

int getCount(const unordered_map<char, int>& m, char c) {
    auto it = m.find(c);
    return (it == m.end()) ? 0 : it->second;
}

int main() {
    string s;
    cin >> s;
    unordered_map<char, int> freq;
    for (char c : s) {
        freq[c] = getCount(freq, c) + 1;
    }
    for (char c = 'a'; c <= 'z'; c++) {
        if (freq.count(c)) cout << c << ":" << freq[c] << " ";
    }
    cout << "\n";
    return 0;
}
```

## Solution 20

### Bug
The fast pointer advances by one step (`fast = fast->next`) just like the slow pointer, so the two are always on the same node and acyclic lists are misreported.

### Explanation
For an acyclic list `1 2 3` built as `3 -> 2 -> 1`, after the first iteration both pointers sit on node 2, the equality test fires, and the program prints `Cycle: true` instead of `Cycle: false`. A single-node list still reports `false` correctly because the loop body never runs. Give the fast pointer a two-step advance.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;
};

void pushFront(Node*& head, int x) {
    head = new Node{x, head};
}

bool hasCycle(Node* head) {
    Node* slow = head;
    Node* fast = head;
    while (fast && fast->next) {
        slow = slow->next;
        fast = fast->next->next;
        if (slow == fast) return true;
    }
    return false;
}

int main() {
    int n, x, makeCycle;
    cin >> n;
    Node* head = nullptr;
    for (int i = 0; i < n; i++) {
        cin >> x;
        pushFront(head, x);
    }
    cin >> makeCycle;
    if (makeCycle) {
        Node* p = head;
        while (p->next) p = p->next;
        p->next = head->next;
    }
    cout << (hasCycle(head) ? "Cycle: true\n" : "Cycle: false\n");
    return 0;
}
```

## Solution 21

### Bug
Both pointers are initialised to the same node and both take one step per loop, so the "slow" pointer simply rides to the end of the list and comes back holding the last node.

### Explanation
For `5 1 2 3 4 5` the list is `5 -> 4 -> 3 -> 2 -> 1` and the middle value is 3. The buggy loop runs the pointer pair together all the way to value 1 and prints `Middle: 1`. A one-node list (`7`) happens to pass because the loop never runs. Speed the fast pointer up to two steps per iteration.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;
};

void pushFront(Node*& head, int x) {
    head = new Node{x, head};
}

int middle(Node* head) {
    Node* slow = head;
    Node* fast = head;
    while (fast && fast->next) {
        slow = slow->next;
        fast = fast->next->next;
    }
    return slow->data;
}

int main() {
    int n, x;
    cin >> n;
    Node* head = nullptr;
    for (int i = 0; i < n; i++) {
        cin >> x;
        pushFront(head, x);
    }
    cout << "Middle: " << middle(head) << "\n";
    return 0;
}
```

## Solution 22

### Bug
`mirror()` swaps the root's children but contains no recursion, so only the top two branches flip and every subtree keeps its own children.

### Explanation
For the tree built from `7 4 2 1 3 6 5 7` (root 4), a correct mirror prints `Inorder: 7 6 5 4 3 2 1`. Only the root's children swap, so the traversal still prints `1 2 3 4 5 6 7`. Recurse on the (now swapped) left and right subtrees after the swap.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

struct TreeNode {
    int data;
    TreeNode* left;
    TreeNode* right;
    TreeNode(int x) : data(x), left(nullptr), right(nullptr) {}
};

void insert(TreeNode*& r, int x) {
    if (!r) {
        r = new TreeNode(x);
        return;
    }
    if (x < r->data) insert(r->left, x);
    else insert(r->right, x);
}

void mirror(TreeNode* r) {
    if (!r) return;
    TreeNode* t = r->left;
    r->left = r->right;
    r->right = t;
    mirror(r->left);
    mirror(r->right);
}

void inorder(TreeNode* r) {
    if (!r) return;
    inorder(r->left);
    cout << r->data << " ";
    inorder(r->right);
}

int main() {
    int n, x;
    cin >> n;
    TreeNode* root = nullptr;
    for (int i = 0; i < n; i++) {
        cin >> x;
        insert(root, x);
    }
    mirror(root);
    cout << "Inorder: ";
    inorder(root);
    cout << "\n";
    return 0;
}
```

## Solution 23

### Bug
Every internal node returns `1 + leaves(left) + leaves(right)`, adding one phantom leaf for each non-leaf node.

### Explanation
In the tree from `7 4 2 1 3 6 5 7` the four real leaves are 1, 3, 5 and 7; internal nodes 4, 2, 6 each add a bogus 1, giving `Leaves: 7` instead of `Leaves: 4`. Drop the extra `1` and return only the sum of the subtrees.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

struct TreeNode {
    int data;
    TreeNode* left;
    TreeNode* right;
    TreeNode(int x) : data(x), left(nullptr), right(nullptr) {}
};

void insert(TreeNode*& r, int x) {
    if (!r) {
        r = new TreeNode(x);
        return;
    }
    if (x < r->data) insert(r->left, x);
    else insert(r->right, x);
}

int countLeaves(TreeNode* r) {
    if (!r) return 0;
    if (!r->left && !r->right) return 1;
    return countLeaves(r->left) + countLeaves(r->right);
}

int main() {
    int n, x;
    cin >> n;
    TreeNode* root = nullptr;
    for (int i = 0; i < n; i++) {
        cin >> x;
        insert(root, x);
    }
    cout << "Leaves: " << countLeaves(root) << "\n";
    return 0;
}
```

## Solution 24

### Bug
The height helper returns `l + rr + 1` instead of the greater child height plus one, so every multi-branch node inflates the values fed into the diameter best-so-far.

### Explanation
For the tree from `7 4 2 1 3 6 5 7` the longest path runs from leaf 1 through nodes 2, 4, 6 to leaf 7 — five nodes. The buggy heights sum the branches: node 2 returns 3, node 6 returns 3, and the root's candidate is `3 + 3 + 1 = 7`, so the program prints `Diameter: 7` instead of `Diameter: 5`. Return `max(l, rr) + 1`.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

struct TreeNode {
    int data;
    TreeNode* left;
    TreeNode* right;
    TreeNode(int x) : data(x), left(nullptr), right(nullptr) {}
};

void insert(TreeNode*& r, int x) {
    if (!r) {
        r = new TreeNode(x);
        return;
    }
    if (x < r->data) insert(r->left, x);
    else insert(r->right, x);
}

int height(TreeNode* r, int& best) {
    if (!r) return 0;
    int l = height(r->left, best);
    int rr = height(r->right, best);
    if (l + rr + 1 > best) best = l + rr + 1;
    return (l > rr ? l : rr) + 1;
}

int diameter(TreeNode* root) {
    int best = 0;
    height(root, best);
    return best;
}

int main() {
    int n, x;
    cin >> n;
    TreeNode* root = nullptr;
    for (int i = 0; i < n; i++) {
        cin >> x;
        insert(root, x);
    }
    cout << "Diameter: " << diameter(root) << "\n";
    return 0;
}
```

## Solution 25

### Bug
The extra base case `if (a == b) return 1;` answers every equal-input pair with GCD 1 instead of the number itself.

### Explanation
For `12 12` the correct answer is `GCD: 12`, but the bogus base case short-circuits to 1. Inputs that are not equal, such as `12 18` (answer 6) or `35 10` (answer 5), still fall through to the correct Euclid step, which is why the bug is easy to miss. Remove the wrong base case; `b == 0` alone is sufficient.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int gcd(int a, int b) {
    if (b == 0) return a;
    return gcd(b, a % b);
}

int main() {
    int a, b;
    cin >> a >> b;
    cout << "GCD: " << gcd(a, b) << "\n";
    return 0;
}
```

## Solution 26

### Bug
The two base cases are swapped: `fib(0)` returns 1 and `fib(1)` returns 0, so the whole sequence slides off by one after that.

### Explanation
Computing `fib(6)` with the buggy bases gives 5 instead of 8, and `fib(10)` gives 34 instead of 55. Input `2` yields 1 either way (`0 + 1`), which hides the problem at the boundary. Return 0 for n = 0 and 1 for n = 1.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int fib(int n) {
    if (n == 0) return 0;
    if (n == 1) return 1;
    return fib(n - 1) + fib(n - 2);
}

int main() {
    int n;
    cin >> n;
    cout << "Fib(" << n << "): " << fib(n) << "\n";
    return 0;
}
```

## Solution 27

### Bug
The recursion adds `n / 10` instead of the extracted digit `n % 10`, so each truncating division is counted over and over.

### Explanation
For `123` the buggy code computes `12 + 1 + 0 = 13` instead of `1 + 2 + 3 = 6`. Input `2024` returns `202 + 20 + 2 = 224` instead of `2 + 0 + 2 + 4 = 8`. Take the last digit with `% 10` and recurse on `n / 10`.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

int sumDigits(int n) {
    if (n == 0) return 0;
    return n % 10 + sumDigits(n / 10);
}

int main() {
    int n;
    cin >> n;
    cout << "Sum: " << sumDigits(n) << "\n";
    return 0;
}
```

## Solution 28

### Bug
The matcher pairs `]` with `{` and `}` with `[`, so the stack comparison checks the wrong closing-bracket/top pairs.

### Explanation
For `[}` the opening `[` is pushed and the closing `}` "matches" it, the stack empties, and `Balanced` is printed even though the pairs are mismatched. For valid `([])`, the inner `]` is compared against `{` (the top is `[`), no branch matches, and the program wrongly prints `Not balanced`. Use the correct pairing for every bracket type.

### Corrected Code

```cpp
#include <iostream>
#include <stack>
#include <string>
using namespace std;

bool isBalanced(const string& s) {
    stack<char> st;
    for (char c : s) {
        if (c == '(' || c == '[' || c == '{') {
            st.push(c);
        } else {
            if (st.empty()) return false;
            char top = st.top();
            if ((c == ')' && top == '(') ||
                (c == ']' && top == '[') ||
                (c == '}' && top == '{')) {
                st.pop();
            } else {
                return false;
            }
        }
    }
    return st.empty();
}

int main() {
    string s;
    cin >> s;
    cout << (isBalanced(s) ? "Balanced\n" : "Not balanced\n");
    return 0;
}
```

## Solution 29

### Bug
The stack-cleanup loop pops while `st.top() < a[i]` but keeps equal values, so a following equal element can be reported as the answer instead of the first strictly greater value.

### Explanation
For `2 2 3` the correct answers are `3 3 -1` from left to right. The buggy pass keeps the equal 2 on the stack, so the last 2 at index 0 is answered with the equal 2 instead of 3, printing `2 3 -1`. Popping equal values too (`<=`) restores the strictly-greater semantics while leaving `4 5 2` untouched (`5 -1 -1`).

### Corrected Code

```cpp
#include <iostream>
#include <vector>
#include <stack>
using namespace std;

int main() {
    int n;
    cin >> n;
    vector<int> a(n);
    for (int i = 0; i < n; i++) cin >> a[i];

    vector<int> res(n, -1);
    stack<int> st;
    for (int i = n - 1; i >= 0; i--) {
        while (!st.empty() && st.top() <= a[i]) st.pop();
        if (!st.empty()) res[i] = st.top();
        st.push(a[i]);
    }

    for (int i = 0; i < n; i++) cout << res[i] << " ";
    cout << "\n";
    return 0;
}
```

## Solution 30

### Bug
Two related bugs: `push()` rejects a value one slot too early (`top + 2 == 5` becomes true when three values are already stored), and `display()` walks from index `top` down to 1, printing the unused zero cell and never printing the element at index 0.

### Explanation
For `4 10 20 30 40` the overflow check fires on the fourth value, so 40 is dropped (`Stack overflow` is printed) and only 10, 20, 30 remain in slots 0–2 with `top` = 3. The loop then prints `data[3]`, `data[2]`, `data[1]` — a stale zero plus 30 and 20 — giving `Stack: 0 30 20` instead of `Stack: 40 30 20 10`. The boundary check must compare against the actual capacity after storing, and the display must start at `top - 1` and end at index 0.

### Corrected Code

```cpp
#include <iostream>
using namespace std;

class Stack {
public:
    int data[5] = {0};
    int top = 0;

    void push(int x) {
        if (top >= 5) {
            cout << "Stack overflow\n";
            return;
        }
        data[top++] = x;
    }

    void display() {
        if (top == 0) {
            cout << "Stack: (empty)\n";
            return;
        }
        cout << "Stack:";
        for (int i = top - 1; i >= 0; i--) cout << " " << data[i];
        cout << "\n";
    }
};

int main() {
    Stack s;
    int n, x;
    cin >> n;
    for (int i = 0; i < n; i++) {
        cin >> x;
        s.push(x);
    }
    s.display();
    return 0;
}
```