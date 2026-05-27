# 44 | Lowest Common Ancestor (Binary Tree)

Find the LCA in a tree WITHOUT the BST properties.

---

## 1. The Objective
Find where paths to $P$ and $Q$ first meet.

---

## 2. Visual Logic
### The "Bubble Up" Strategy
1. Search recursively for $P$ or $Q$.
2. If a node finds $P$ on left and $Q$ on right: **It is the LCA**.
3. If it finds only one: Pass that node up.

---

## 3. The "Aha!" Moment
In a generic tree, we use recursion to signal "I found it" from the bottom up. The node that receives signals from both branches is the ancestor.

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

TreeNode* LCA(TreeNode* root, TreeNode* p, TreeNode* q) {
    if (!root || root == p || root == q) return root;
    
    TreeNode* left = LCA(root->left, p, q);
    TreeNode* right = LCA(root->right, p, q);
    
    if (left && right) return root; // Found in both branches
    return left ? left : right;      // Pass up the one found
}
```
