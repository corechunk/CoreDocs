# 17 | In-order Predecessor in BST

Find the node that comes immediately before $X$ in a sorted traversal.

---

## 1. The Objective
Given $X$, find the next smallest value.

---

## 2. Visual Logic
Opposite of Successor:
1. If $X$ has a **Left Child**: Predecessor is the `max()` of that left subtree.
2. If NO left child: Predecessor is the **lowest ancestor** where $X$ is in the right subtree.

---

## 3. The "Aha!" Moment
Mirrors the Successor logic precisely.

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

TreeNode* inorderPredecessor(TreeNode* root, TreeNode* p) {
    TreeNode* predecessor = nullptr;
    while (root) {
        if (p->val > root->val) {
            predecessor = root;
            root = root->right;
        } else {
            root = root->left;
        }
    }
    return predecessor;
}
```
