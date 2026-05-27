# 🌿 Binary Tree (The Power of Two)

## 1. The Objective
A Binary Tree is a specific type of tree where **each node can have at most two children**, typically called the `left` child and the `right` child. It is the foundation for many complex data structures like BSTs, Heaps, and Segment Trees.

---

## 2. Visual Logic
### Binary Structure
```text
        [Root]
       /      \
    [Left]   [Right]
    /    \       \
 [L.L]  [L.R]   [R.R]
```

### Types of Binary Trees
- **Full Binary Tree:** Every node has either 0 or 2 children.
- **Complete Binary Tree:** All levels are filled except possibly the last, which is filled from left to right.
- **Perfect Binary Tree:** All internal nodes have 2 children and all leaves are at the same level.

---

## 3. The "Aha!" Moment
- **Recursive Nature:** A Binary Tree is either empty or consists of a root and two binary subtrees. This makes recursion the most natural way to traverse and manipulate them.
- **Traversals:** 
    - **In-order (L, Root, R):** Used in BSTs to get sorted data.
    - **Pre-order (Root, L, R):** Used to create a copy of the tree.
    - **Post-order (L, R, Root):** Used to delete the tree (children before parent).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Standard Binary Node)

```cpp
#include <iostream>

struct Node {
    int data;
    Node *left, *right;

    Node(int val) : data(val), left(nullptr), right(nullptr) {}
};

// In-order Traversal (Left, Root, Right)
void inOrder(Node* root) {
    if (!root) return;
    inOrder(root->left);
    std::cout << root->data << " ";
    inOrder(root->right);
}

int main() {
    Node* root = new Node(1);
    root->left = new Node(2);
    root->right = new Node(3);
    root->left->left = new Node(4);
    root->left->right = new Node(5);

    std::cout << "In-order Traversal: ";
    inOrder(root);
    std::cout << std::endl;

    return 0;
}
```

---
[➔ Back to Tree Hub](tree.md) | [➔ Back to Roadmap](../DSA-Master-Roadmap.md)
