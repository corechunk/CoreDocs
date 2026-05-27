# ⚖️ AVL Tree (Height-Balanced BST)

## 1. The Objective
An AVL Tree (named after inventors Adelson-Velsky and Landis) is a self-balancing Binary Search Tree. It ensures that the height difference (Balance Factor) between left and right subtrees is at most **1**, guaranteeing $O(\log n)$ performance for all operations even in the worst case.

---

## 2. Visual Logic
### The Balance Factor (BF)
`BF = height(left) - height(right)`
- Must be `-1`, `0`, or `1`.

### Rotations (Fixing BF > 1 or BF < -1)
- **Single Rotation:** LL (Left-Left) or RR (Right-Right).
- **Double Rotation:** LR (Left-Right) or RL (Right-Left).

---

## 3. The Logic Bridge
- **Why it's needed:** A standard BST can degrade into a linked list ($O(n)$) if items are inserted in sorted order. AVL trees "re-balance" themselves automatically by rotating nodes, keeping the tree "bushy" and the height logarithmic.
- **The Tradeoff:** AVL trees provide faster lookups than Red-Black trees (because they are more strictly balanced) but might have slower insertions/deletions due to more frequent rotations.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Rotations)

```cpp
#include <iostream>
#include <algorithm>

struct Node {
    int key, height;
    Node *left, *right;
    Node(int k) : key(k), height(1), left(nullptr), right(nullptr) {}
};

int getHeight(Node* n) { return n ? n->height : 0; }
int getBalance(Node* n) { return n ? getHeight(n->left) - getHeight(n->right) : 0; }

Node* rightRotate(Node* y) {
    Node* x = y->left;
    Node* T2 = x->right;
    x->right = y;
    y->left = T2;
    y->height = std::max(getHeight(y->left), getHeight(y->right)) + 1;
    x->height = std::max(getHeight(x->left), getHeight(x->right)) + 1;
    return x;
}

Node* leftRotate(Node* x) {
    Node* y = x->right;
    Node* T2 = y->left;
    y->left = x;
    x->right = T2;
    x->height = std::max(getHeight(x->left), getHeight(x->right)) + 1;
    y->height = std::max(getHeight(y->left), getHeight(y->right)) + 1;
    return y;
}

// Full AVL Insertion logic would go here...
```

---
[➔ Back to Tree Hub](tree.md) | [➔ Back to Roadmap](../DSA-Master-Roadmap.md)
