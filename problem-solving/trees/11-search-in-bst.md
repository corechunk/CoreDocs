# 11 | Search in BST

Efficiently find a value in a Binary Search Tree.

---

## 1. The Objective
Find target $X$ in a tree where:
- Left child $<$ Parent
- Right child $>$ Parent

---

## 2. Visual Logic
### The "Decision" Strategy
1. Compare $X$ with Root.
2. If $X <$ Root: Go **Left** only.
3. If $X >$ Root: Go **Right** only.

---

## 3. The "Aha!" Moment
Because of the sorted structure, you ignore half the tree at every step. This makes search $O(h)$, which is $O(\log n)$ for a balanced tree.

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

/**
 * Strategy: Divide and Conquer
 */
TreeNode* searchBST(TreeNode* root, int val) {
    if (!root || root->val == val) return root;
    
    if (val < root->val) return searchBST(root->left, val);
    return searchBST(root->right, val);
}

int main() {
    // Logic...
    return 0;
}
```
