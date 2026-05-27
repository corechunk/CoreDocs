# 38 | Check if Subtree

Determine if Tree S is contained within Tree T.

---

## 1. The Objective
Is one tree a smaller part of another?

---

## 2. Visual Logic
1. If current Root of T matches Root of S, check if they are **Identical** (Problem 30).
2. If NOT, check if S is a subtree of T's Left child OR T's Right child.

---

## 3. The "Aha!" Moment
This is recursion inside recursion. You search for the "Head" of the subtree and then verify the full structure.

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

bool isSame(TreeNode* s, TreeNode* t) {
    if (!s && !t) return true;
    if (!s || !t || s->val != t->val) return false;
    return isSame(s->left, t->left) && isSame(s->right, t->right);
}

bool isSubtree(TreeNode* root, TreeNode* sub) {
    if (!root) return false;
    if (isSame(root, sub)) return true;
    return isSubtree(root->left, sub) || isSubtree(root->right, sub);
}
```
