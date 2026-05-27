# 39 | Sum of All Nodes

Calculate the grand total of values in a tree.

---

## 1. The Objective
Add every integer in every node.

---

## 2. Visual Logic
Total = `root->val + sum(left) + sum(right)`.

---

## 3. The "Aha!" Moment
Simple Pre-order or Post-order traversal. This is the tree version of summing a 1D array.

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

long long treeSum(TreeNode* root) {
    if (!root) return 0;
    return root->val + treeSum(root->left) + treeSum(root->right);
}
```
