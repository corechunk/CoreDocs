# 19 | Range Sum in BST

Calculate the sum of all node values between `L` and `R`.

---

## 1. The Objective
Given `[10, 5, 15, 3, 7, 18]` and `L=7, R=15`, return `7 + 10 + 15 = 32`.

---

## 2. Visual Logic
### The "Pruning" Strategy
- If Root $<$ L: Go Right only.
- If Root $>$ R: Go Left only.
- If in range: Add Root + Left + Right.

---

## 3. The "Aha!" Moment
Don't visit the whole tree. If the root is already smaller than your minimum, everything on its left is also smaller. Skip them!

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

int rangeSumBST(TreeNode* root, int L, int R) {
    if (!root) return 0;
    
    if (root->val < L) return rangeSumBST(root->right, L, R);
    if (root->val > R) return rangeSumBST(root->left, L, R);
    
    return root->val + rangeSumBST(root->left, L, R) + rangeSumBST(root->right, L, R);
}
```
