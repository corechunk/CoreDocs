# 30 | Identical Trees Check

Determine if two trees are structurally and value-wise identical.

---

## 1. The Objective
Return true if $T_1 == T_2$.

---

## 2. Visual Logic
### The "Recursive Match"
1. Roots match?
2. $T_1 \to$ Left matches $T_2 \to$ Left?
3. $T_1 \to$ Right matches $T_2 \to$ Right?

---

## 3. The "Aha!" Moment
Same logic as "Check Symmetric" (Problem 22), but without the mirrored index flip.

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

bool isSameTree(TreeNode* p, TreeNode* q) {
    if (!p && !q) return true;
    if (!p || !q || p->val != q->val) return false;
    
    return isSameTree(p->left, q->left) && isSameTree(p->right, q->right);
}
```
