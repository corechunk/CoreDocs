# 50 | Morris In-order Traversal

Visit nodes in-order with $O(1)$ space (no recursion stack).

---

## 1. The Objective
Traverse the tree without using extra memory for recursion or a stack.

---

## 2. Visual Logic
### The "Temporary Link" Strategy
1. For every node, find its **In-order Predecessor** (rightmost node in left subtree).
2. Create a temporary "thread" (link) from the predecessor back to the current node.
3. This allows you to climb back up without a stack.
4. Delete the link once you return.

---

## 3. The "Aha!" Moment
Morris traversal "borrows" the NULL pointers of leaf nodes to store the way back to the parents. This is the absolute peak of traversal optimization.

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

void morrisInOrder(TreeNode* root) {
    TreeNode* curr = root;
    while (curr) {
        if (!curr->left) {
            std::cout << curr->val << " ";
            curr = curr->right;
        } else {
            TreeNode* pre = curr->left;
            while (pre->right && pre->right != curr) pre = pre->right;
            
            if (!pre->right) {
                pre->right = curr; // Create thread
                curr = curr->left;
            } else {
                pre->right = nullptr; // Fix thread
                std::cout << curr->val << " ";
                curr = curr->right;
            }
        }
    }
}
```
