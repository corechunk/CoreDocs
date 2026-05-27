# 42 | Next Right Pointers

Connect nodes on the same level like a linked list.

---

## 1. The Objective
For each node, set its `next` pointer to the node to its immediate right.

---

## 2. Visual Logic
### The "Breadth" Link
In BFS, as you process a level, the next node in the queue is your `next` neighbor.

---

## 3. The "Aha!" Moment
If you have a Perfect Binary Tree, your left child's `next` is always your right child.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <queue>

struct Node {
    int val;
    Node *left, *right, *next;
    Node(int x) : val(x), left(NULL), right(NULL), next(NULL) {}
};

void connect(Node* root) {
    if (!root) return;
    std::queue<Node*> q;
    q.push(root);
    
    while (!q.empty()) {
        int size = q.size();
        for (int i = 0; i < size; i++) {
            Node* curr = q.front(); q.pop();
            if (i < size - 1) curr->next = q.front();
            
            if (curr->left) q.push(curr->left);
            if (curr->right) q.push(curr->right);
        }
    }
}
```
