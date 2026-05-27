# 03 | In-order Traversal

Visit nodes in the order: **Left $\to$ Root $\to$ Right**.

---

## 1. The Objective
Produce a sorted-like output for Binary Search Trees.

---

## 2. Visual Logic
### The "Leftmost-First" Scan
```text
      1
     / \
    2   3
```
Order: **2, 1, 3**

---

## 3. The "Aha!" Moment
If the tree is a Binary Search Tree (BST), In-order traversal will **always** print the numbers in non-decreasing sorted order.

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
 * Strategy: Recursive In-order
 */
void inOrder(TreeNode* root) {
    if (!root) return;
    
    inOrder(root->left);           // Left
    std::cout << root->val << " "; // Root
    inOrder(root->right);          // Right
}

int main() {
    // 2 is left of 1...
    return 0;
}
```
