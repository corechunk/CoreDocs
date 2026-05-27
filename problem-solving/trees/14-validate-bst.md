# 14 | Validate BST

Verify if a Binary Tree is a valid Binary Search Tree.

---

## 1. The Objective
Check if every node satisfies the $(Left < Root < Right)$ condition globally.

---

## 2. Visual Logic
### The "Constraint" Strategy
Each node must fall within a range `[min, max]`.
- Root can be anything.
- Left child of 10 must be `[-inf, 10]`.
- Right child of 10 must be `[10, +inf]`.

---

## 3. The "Aha!" Moment
A simple local check `(node->left < node)` is NOT enough. A node far down in the left subtree could still be larger than the root. You must pass bounds down recursively.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <climits>

struct TreeNode {
    int val;
    TreeNode *left, *right;
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
};

bool validate(TreeNode* root, long long min, long long max) {
    if (!root) return true;
    if (root->val <= min || root->val >= max) return false;
    
    return validate(root->left, min, root->val) && 
           validate(root->right, root->val, max);
}

int main() {
    // validate(root, LLONG_MIN, LLONG_MAX);
    return 0;
}
```
