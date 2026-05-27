# 29 | Diameter of Binary Tree

Find the longest path between any two nodes.

---

## 1. The Objective
The path does not have to pass through the root.

---

## 2. Visual Logic
### The "Split" Strategy
For every node, the longest path passing through it is:
`height(left) + height(right)`.
The diameter of the tree is the **maximum** such value found across all nodes.

---

## 3. The "Aha!" Moment
Similar to "Check Balanced" (Problem 21), calculate height and update a global maximum diameter simultaneously in one pass.

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

int getDiameter(TreeNode* root, int& maxD) {
    if (!root) return 0;
    
    int lh = getDiameter(root->left, maxD);
    int rh = getDiameter(root->right, maxD);
    
    maxD = std::max(maxD, lh + rh);
    return 1 + std::max(lh, rh);
}

int diameter(TreeNode* root) {
    int maxD = 0;
    getDiameter(root, maxD);
    return maxD;
}
```
