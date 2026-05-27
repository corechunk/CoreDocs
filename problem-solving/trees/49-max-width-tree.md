# 49 | Maximum Width of Tree

Find the maximum number of nodes (including NULLs) between the leftmost and rightmost nodes on any level.

---

## 1. The Objective
Calculate the maximum "Span" of any level.

---

## 2. Visual Logic
### The "Binary Indexing" Strategy
Assign an index to each node:
- Root: `1`
- Left: `2*index`
- Right: `2*index + 1`
Width of level = `RightmostIndex - LeftmostIndex + 1`.

---

## 3. The "Aha!" Moment
By using indices, you can calculate the distance even if the space between nodes is empty (filled with NULLs).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <queue>
#include <algorithm>

struct TreeNode {
    int val;
    TreeNode *left, *right;
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
};

int widthOfBinaryTree(TreeNode* root) {
    if (!root) return 0;
    long long maxWidth = 0;
    std::queue<std::pair<TreeNode*, long long>> q;
    q.push({root, 0});
    
    while (!q.empty()) {
        int size = q.size();
        long long first, last;
        long long minIdx = q.front().second; // To prevent overflow
        for (int i = 0; i < size; i++) {
            long long curIdx = q.front().second - minIdx;
            TreeNode* node = q.front().first; q.pop();
            if (i == 0) first = curIdx;
            if (i == size - 1) last = curIdx;
            if (node->left) q.push({node->left, curIdx * 2 + 1});
            if (node->right) q.push({node->right, curIdx * 2 + 2});
        }
        maxWidth = std::max(maxWidth, last - first + 1);
    }
    return maxWidth;
}
```
