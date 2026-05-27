# 24 | Right View of Binary Tree

Identify nodes visible from the right side.

---

## 1. The Objective
Print the last node of every level.

---

## 2. Visual Logic
Opposite of Left View:
1. Visit **Right** child first.
2. If `level == res.size()`, it's the first time seeing this depth from the right.

---

## 3. The "Aha!" Moment
By reversing the order of recursion (Right before Left), the first node encountered at any level is the one on the extreme right.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

struct TreeNode {
    int val;
    TreeNode *left, *right;
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
};

void getRightView(TreeNode* root, int level, std::vector<int>& res) {
    if (!root) return;
    
    if (level == res.size()) res.push_back(root->val);
    
    getRightView(root->right, level + 1, res);
    getRightView(root->left, level + 1, res);
}
```
