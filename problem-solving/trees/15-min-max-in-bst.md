# 15 | Min/Max in BST

Find the extreme values in a Binary Search Tree.

---

## 1. The Objective
Return the smallest and largest values.

---

## 2. Visual Logic
- **Min:** Go **Left** as much as possible.
- **Max:** Go **Right** as much as possible.

---

## 3. The "Aha!" Moment
In a BST, the leftmost node is the absolute minimum, and the rightmost is the absolute maximum. $O(h)$ complexity.

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

int getBSTMin(TreeNode* root) {
    if (!root) return -1;
    while (root->left) root = root->left;
    return root->val;
}

int getBSTMax(TreeNode* root) {
    if (!root) return -1;
    while (root->right) root = root->right;
    return root->val;
}
```
