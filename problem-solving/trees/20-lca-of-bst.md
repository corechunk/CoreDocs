# 20 | Lowest Common Ancestor (BST)

Find the lowest node that has both `P` and `Q` as descendants.

---

## 1. The Objective
Find the "split point" of two values.

---

## 2. Visual Logic
### The "BST Split" Strategy
Traverse from the top:
1. If both $P, Q <$ Root: Go **Left**.
2. If both $P, Q >$ Root: Go **Right**.
3. If one is smaller and one is larger: **The current Root is the LCA**.

---

## 3. The "Aha!" Moment
In a BST, the LCA is the first node where the two paths diverge.

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

TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
    if (p->val < root->val && q->val < root->val)
        return lowestCommonAncestor(root->left, p, q);
    if (p->val > root->val && q->val > root->val)
        return lowestCommonAncestor(root->right, p, q);
    
    return root;
}
```
