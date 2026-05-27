# 25 | Top View of Tree

Identify nodes visible from the top.

---

## 1. The Objective
Think of the tree on a coordinate plane where root is $X=0$. Print one node for each unique $X$ coordinate.

---

## 2. Visual Logic
### The "Horizontal Distance" Map
1. Use BFS.
2. Store `(Node, HorizontalDistance)`.
   - Left child: `dist - 1`.
   - Right child: `dist + 1`.
3. Keep only the **First** node seen for each distance.

---

## 3. The "Aha!" Moment
Vertical levels allow you to project the tree into a 1D silhouette from above.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <map>
#include <queue>

struct TreeNode {
    int val;
    TreeNode *left, *right;
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
};

void topView(TreeNode* root) {
    if (!root) return;
    std::map<int, int> m;
    std::queue<std::pair<TreeNode*, int>> q;
    q.push({root, 0});
    
    while (!q.empty()) {
        auto p = q.front(); q.pop();
        TreeNode* node = p.first;
        int dist = p.second;
        
        if (m.find(dist) == m.end()) m[dist] = node->val;
        
        if (node->left) q.push({node->left, dist - 1});
        if (node->right) q.push({node->right, dist + 1});
    }
    for (auto const& [dist, val] : m) std::cout << val << " ";
}
```
