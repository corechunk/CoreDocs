# 16 | In-order Successor in BST

Find the node that comes immediately after $X$ in a sorted traversal.

---

## 1. The Objective
Given target $X$, what is the next largest value?

---

## 2. Visual Logic
1. If $X$ has a **Right Child**: Successor is the `min()` of that right subtree.
2. If NO right child: Successor is the **lowest ancestor** where $X$ is in the left subtree.

---

## 3. The "Aha!" Moment
Think of In-order successor as the value you'd see next if you printed the tree.

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

TreeNode* inorderSuccessor(TreeNode* root, TreeNode* p) {
    TreeNode* successor = nullptr;
    while (root) {
        if (p->val < root->val) {
            successor = root;
            root = root->left;
        } else {
            root = root->right;
        }
    }
    return successor;
}
```
