# 48 | Minimum Depth of Tree

Find the shortest path from root to a leaf node.

---

## 1. The Objective
Return the smallest level count.

---

## 2. Visual Logic
### The "BFS Winner"
The first time Level-order traversal (BFS) hits a **Leaf Node**, that node's level is the minimum depth.

---

## 3. The "Aha!" Moment
BFS is better than DFS here because it explores breadth-first. You don't have to check the entire tree if a shallow leaf exists.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <queue>

struct TreeNode {
    int val;
    TreeNode *left, *right;
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
};

int minDepth(TreeNode* root) {
    if (!root) return 0;
    std::queue<std::pair<TreeNode*, int>> q;
    q.push({root, 1});
    
    while (!q.empty()) {
        auto p = q.front(); q.pop();
        TreeNode* node = p.first;
        int d = p.second;
        
        if (!node->left && !node->right) return d; // Found first leaf
        
        if (node->left) q.push({node->left, d + 1});
        if (node->right) q.push({node->right, d + 1});
    }
    return 0;
}
```
