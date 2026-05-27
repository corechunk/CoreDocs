# 35 | Flatten Tree to Linked List

Convert a tree into a "line" (only right pointers) in pre-order.

---

## 1. The Objective
restructure the tree so every node's `left` is NULL and `right` points to the next node in pre-order.

---

## 2. Visual Logic
### The "Thread" Strategy
1. Flatten left subtree.
2. Flatten right subtree.
3. Attach flattened right to the tail of flattened left.
4. Set root's right to flattened left.

---

## 3. The "Aha!" Moment
You are essentially performing a surgery to turn a 2D branching structure into a 1D sequence using the existing pointers.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

struct TreeNode {
    int val;
    TreeNode *left, *right;
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
};

void flatten(TreeNode* root) {
    if (!root) return;
    
    flatten(root->left);
    flatten(root->right);
    
    TreeNode* tempRight = root->right;
    root->right = root->left;
    root->left = nullptr;
    
    TreeNode* curr = root;
    while (curr->right) curr = curr->right;
    curr->right = tempRight;
}
```
