# 26 | Bottom View of Tree

Identify nodes visible from underneath.

---

## 1. The Objective
The opposite of Top View.

---

## 2. Visual Logic
### The "Overwrite" Strategy
1. Use BFS with horizontal distance.
2. Instead of only keeping the first, **always overwrite** the value for that distance.
3. The last node processed at each $X$ coordinate is the one visible from the bottom.

---

## 3. The "Aha!" Moment
BFS processes level-by-level, so the "last" node seen for any vertical line is guaranteed to be the lowest.

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

void bottomView(TreeNode* root) {
    if (!root) return;
    std::map<int, int> m;
    std::queue<std::pair<TreeNode*, int>> q;
    q.push({root, 0});
    
    while (!q.empty()) {
        auto p = q.front(); q.pop();
        int dist = p.second;
        m[dist] = p.first->val; // Overwrite
        
        if (p.first->left) q.push({p.first->left, dist - 1});
        if (p.first->right) q.push({p.first->right, dist + 1});
    }
    // Print map...
}
```
