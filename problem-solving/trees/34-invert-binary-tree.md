# 34 | Invert Binary Tree (Mirror)

Flip every left and right child in the tree.

---

## 1. The Objective
Transform the tree into its mirror image.

---

## 2. Visual Logic
### The "Swap" Step
1. Go to current node.
2. Swap its `left` and `right` pointers.
3. Recursively do the same for children.

---

## 3. The "Aha!" Moment
This is a **Post-order** (or Pre-order) traversal where the operation is a simple swap.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <algorithm>

struct TreeNode {
    int val;
    TreeNode *left, *right;
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
};

TreeNode* invertTree(TreeNode* root) {
    if (!root) return nullptr;
    
    // Swap pointers
    TreeNode* temp = root->left;
    root->left = root->right;
    root->right = temp;
    
    invertTree(root->left);
    invertTree(root->right);
    
    return root;
}
```
