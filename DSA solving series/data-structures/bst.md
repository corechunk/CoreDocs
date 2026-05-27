# 🔍 Binary Search Tree (BST)

## 1. The Objective
A Binary Search Tree (BST) is a binary tree with a **sorting property**: For every node, all values in the left subtree are smaller, and all values in the right subtree are larger. This structure enables search, insertion, and deletion in $O(\log n)$ time on average.

---

## 2. Visual Logic
### The BST Property
```text
        [15]
       /    \
    [10]    [20]
   /   \    /   \
 [8]  [12][17]  [25]
```
- **In-order Traversal Result:** `8, 10, 12, 15, 17, 20, 25` (Always Sorted!)

---

## 3. The "Aha!" Moment
- **Search Efficiency:** Searching a BST is exactly like Binary Search on a sorted array. At each node, you eliminate half of the tree by comparing the key.
- **Dynamic Sorting:** Unlike a sorted array, which requires $O(n)$ time to insert/delete, a BST allows these operations in $O(\log n)$ while keeping the data sorted.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (BST Ops)

```cpp
#include <iostream>

struct Node {
    int data;
    Node *left, *right;
    Node(int val) : data(val), left(nullptr), right(nullptr) {}
};

// Recursive Insertion
Node* insert(Node* root, int val) {
    if (!root) return new Node(val);
    if (val < root->data)
        root->left = insert(root->left, val);
    else if (val > root->data)
        root->right = insert(root->right, val);
    return root;
}

// Search Operation
bool search(Node* root, int key) {
    if (!root) return false;
    if (root->data == key) return true;
    if (key < root->data) return search(root->left, key);
    return search(root->right, key);
}

int main() {
    Node* root = nullptr;
    int values[] = {15, 10, 20, 8, 12, 17, 25};
    
    for (int v : values) root = insert(root, v);

    std::cout << "Search for 17: " << (search(root, 17) ? "Found" : "Not Found") << std::endl;
    std::cout << "Search for 30: " << (search(root, 30) ? "Found" : "Not Found") << std::endl;

    return 0;
}
```

---
[➔ Back to Tree Hub](tree.md) | [➔ Back to Roadmap](../DSA-Master-Roadmap.md)
