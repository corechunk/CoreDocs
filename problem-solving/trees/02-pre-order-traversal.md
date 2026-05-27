# 02 | Pre-order Traversal

Visit nodes in the order: **Root $\to$ Left $\to$ Right**.

---

## 1. The Objective
Given a tree, print its values using the Pre-order strategy.

---

## 2. Visual Logic
### The "Top-Down" Scan
```text
      1
     / \
    2   3
   / \
  4   5
```
Order: **1, 2, 4, 5, 3**

---

## 3. The "Aha!" Moment
Recursion handles the stack for you. 
1. "Process" the current node.
2. Tell the Left child to do the same.
3. Tell the Right child to do the same.

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
 * Strategy: Recursive Pre-order
 * Efficiency: Time O(n), Space O(h) where h is height
 */
void preOrder(TreeNode* root) {
    if (!root) return;
    
    std::cout << root->val << " "; // Root
    preOrder(root->left);           // Left
    preOrder(root->right);          // Right
}

int main() {
    TreeNode* root = new TreeNode(1);
    root->left = new TreeNode(2);
    root->right = new TreeNode(3);
    preOrder(root);
    return 0;
}
```
