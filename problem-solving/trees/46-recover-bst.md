# 46 | Recover BST

Fix a BST where exactly two nodes have been swapped by mistake.

---

## 1. The Objective
Given a "broken" BST, identify the two nodes and swap their values back.

---

## 2. Visual Logic
### The "Sorted Violation"
Perform In-order traversal. Look for elements that are smaller than the previous element.
- `[1, 5, 3, 4, 2, 6]`
- Violations: `5 > 3` and `4 > 2`.
Swap 5 and 2.

---

## 3. The "Aha!" Moment
The first violation is the "High" value that moved left. The second violation is the "Low" value that moved right.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <algorithm>

struct TreeNode {
    int val;
    TreeNode *left, *right;
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
};

TreeNode *first=NULL, *second=NULL, *prev=NULL;

void findSwapped(TreeNode* root) {
    if (!root) return;
    findSwapped(root->left);
    
    if (prev && root->val < prev->val) {
        if (!first) first = prev;
        second = root;
    }
    prev = root;
    
    findSwapped(root->right);
}

void recoverTree(TreeNode* root) {
    findSwapped(root);
    std::swap(first->val, second->val);
}
```
