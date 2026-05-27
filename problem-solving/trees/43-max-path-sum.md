# 43 | Maximum Path Sum (Any Node)

Find the highest sum of a path starting and ending at any two nodes.

---

## 1. The Objective
The path can curve and does not need to involve the root.

---

## 2. Visual Logic
### The "Bridge" Max
For any node:
1. Max if I am the **Endpoint** of a path: `val + max(left, right)`.
2. Max if I am the **Bridge** (center) of a path: `val + left + right`.
Keep track of global max.

---

## 3. The "Aha!" Moment
A node can either pass its best branch up to its parent, or it can "complete" a path between its two children.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <algorithm>
#include <climits>

struct TreeNode {
    int val;
    TreeNode *left, *right;
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
};

int solve(TreeNode* root, int& res) {
    if (!root) return 0;
    
    int l = std::max(0, solve(root->left, res)); // Max contribution
    int r = std::max(0, solve(root->right, res));
    
    res = std::max(res, root->val + l + r); // Bridge sum
    return root->val + std::max(l, r);      // Branch sum
}
```
