# 27 | Zig-zag Level Order Traversal

Traverse level by level, but flip the direction at each step.

---

## 1. The Objective
Given:
```text
    1
   / \
  2   3
 / \ / \
4  5 6  7
```
Output: `1, 3, 2, 4, 5, 6, 7`

---

## 2. Visual Logic
### The "Flag" Flip
1. Standard BFS.
2. For each level:
   - Store nodes in a list.
   - If `level % 2 != 0`, reverse the list before adding to result.

---

## 3. The "Aha!" Moment
Alternatively, use two **Stacks** to avoid the explicit reverse step. One stack for Left-to-Right, one for Right-to-Left.

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

void zigzagOrder(TreeNode* root) {
    if (!root) return;
    std::queue<TreeNode*> q;
    q.push(root);
    bool leftToRight = true;
    
    while (!q.empty()) {
        int size = q.size();
        std::vector<int> row(size);
        for (int i = 0; i < size; i++) {
            TreeNode* node = q.front(); q.pop();
            int index = leftToRight ? i : (size - 1 - i);
            row[index] = node->val;
            
            if (node->left) q.push(node->left);
            if (node->right) q.push(node->right);
        }
        leftToRight = !leftToRight;
        for(int x : row) std::cout << x << " ";
    }
}
```
