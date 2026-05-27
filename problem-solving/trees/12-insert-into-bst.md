# 12 | Insert into BST

Add a new value while maintaining the BST properties.

---

## 1. The Objective
Place $X$ in the correct leaf position.

---

## 2. Visual Logic
Similar to searching:
- If $X <$ Root, go Left.
- If $X >$ Root, go Right.
- When you hit `NULL`, create the new node there.

---

## 3. The "Aha!" Moment
A new node is always inserted as a **Leaf**. You just have to find the correct empty spot.

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

TreeNode* insertBST(TreeNode* root, int val) {
    if (!root) return new TreeNode(val);
    
    if (val < root->val) {
        root->left = insertBST(root->left, val);
    } else {
        root->right = insertBST(root->right, val);
    }
    return root;
}

int main() {
    // Logic...
    return 0;
}
```
