# 22 | Check if Symmetric

Verify if a tree is a mirror image of itself.

---

## 1. The Objective
Check if the left side of the root is the mirror of the right side.

---

## 2. Visual Logic
### The "Mirror Comparison"
To be mirrors, two trees $T_1$ and $T_2$ must:
1. Have the same root value.
2. $T_1 \to$ Left must mirror $T_2 \to$ Right.
3. $T_1 \to$ Right must mirror $T_2 \to$ Left.

---

## 3. The "Aha!" Moment
This is a recursive check on **Two Trees** simultaneously.

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

bool isMirror(TreeNode* t1, TreeNode* t2) {
    if (!t1 && !t2) return true;
    if (!t1 || !t2) return false;
    
    return (t1->val == t2->val) && 
           isMirror(t1->left, t2->right) && 
           isMirror(t1->right, t2->left);
}

bool isSymmetric(TreeNode* root) {
    return isMirror(root, root);
}
```
