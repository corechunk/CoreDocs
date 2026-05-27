# 40 | Find Depth of a Node

Determine how far a specific node is from the root.

---

## 1. The Objective
Given target $X$, return its level (Root is 0).

---

## 2. Visual Logic
1. If I am the target, depth is 0.
2. If target is in Left, depth is `1 + leftDepth`.
3. If target is in Right, depth is `1 + rightDepth`.

---

## 3. The "Aha!" Moment
Pass a `current_depth` variable down. The moment you find the node, that variable is your answer.

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

int getDepth(TreeNode* root, int x, int d) {
    if (!root) return -1;
    if (root->val == x) return d;
    
    int ld = getDepth(root->left, x, d + 1);
    if (ld != -1) return ld;
    
    return getDepth(root->right, x, d + 1);
}
```
