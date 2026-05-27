# 23 | Left View of Binary Tree

Identify nodes visible from the left side.

---

## 1. The Objective
Print the first node of every level.

---

## 2. Visual Logic
### The "First at Level" Strategy
Use Level-order traversal (BFS) and only print the first element of each queue snapshot.

---

## 3. The "Aha!" Moment
If you use DFS, you can pass the `level` down. If `level == result.size()`, this is the first time you've visited this depth.

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

void getLeftView(TreeNode* root, int level, std::vector<int>& res) {
    if (!root) return;
    
    if (level == res.size()) {
        res.push_back(root->val);
    }
    
    getLeftView(root->left, level + 1, res);
    getLeftView(root->right, level + 1, res);
}
```
