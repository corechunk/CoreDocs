# 45 | Binary Tree to BST Conversion

Transform any binary tree into a BST without changing the structure.

---

## 1. The Objective
Keep the node links identical, but rearrange values to satisfy BST rules.

---

## 2. Visual Logic
1. Perform In-order traversal and store all values in an array.
2. Sort the array.
3. Perform a **second** In-order traversal and put the sorted values back into the nodes.

---

## 3. The "Aha!" Moment
Since In-order traversal of a BST is always sorted, extracting values, sorting them, and re-inserting them via In-order **guarantees** the result is a BST.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

struct TreeNode {
    int val;
    TreeNode *left, *right;
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
};

void collect(TreeNode* root, std::vector<int>& v) {
    if (!root) return;
    collect(root->left, v);
    v.push_back(root->val);
    collect(root->right, v);
}

void putBack(TreeNode* root, std::vector<int>& v, int& idx) {
    if (!root) return;
    putBack(root->left, v, idx);
    root->val = v[idx++];
    putBack(root->right, v, idx);
}
```
