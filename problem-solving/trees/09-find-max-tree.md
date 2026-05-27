# 09 | Find Maximum in Tree

Identify the highest value in an unsorted Binary Tree.

---

## 1. The Objective
Return the max value among all nodes.

---

## 2. Visual Logic
Max = `max(root->val, max(leftMax, rightMax))`.

---

## 3. The "Aha!" Moment
Unlike a BST where you just go right, in a normal tree, you must check **every** node because the max could be anywhere.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <algorithm>
#include <climits>

struct TreeNode {
    int val;
    TreeNode *left, *right;
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
};

int findMax(TreeNode* root) {
    if (!root) return INT_MIN;
    
    int res = root->val;
    int lres = findMax(root->left);
    int rres = findMax(root->right);
    
    return std::max({res, lres, rres});
}

int main() {
    // Logic...
    return 0;
}
```
