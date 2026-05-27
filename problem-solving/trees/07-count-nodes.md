# 07 | Count Total Nodes

Find the total number of elements in the tree.

---

## 1. The Objective
Count every node from root to leaf.

---

## 2. Visual Logic
### The "Census" Strategy
Nodes in Root = $1 + \text{Nodes in Left} + \text{Nodes in Right}$.

---

## 3. The "Aha!" Moment
Another recursive reduction. Every node "contributes" 1 to the total sum of its subtrees.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

struct TreeNode {
    int val;
    TreeNode *left, *right;
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
};

int countNodes(TreeNode* root) {
    if (!root) return 0;
    return 1 + countNodes(root->left) + countNodes(root->right);
}

int main() {
    // Logic...
    return 0;
}
```
