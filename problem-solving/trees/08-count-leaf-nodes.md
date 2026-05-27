# 08 | Count Leaf Nodes

Identify and count nodes that have zero children.

---

## 1. The Objective
Find the "ends" of the branches.

---

## 2. Visual Logic
### The "Dead-End" Rule
A node is a leaf IF `left == NULL` AND `right == NULL`.

---

## 3. The "Aha!" Moment
Skip all nodes that have at least one child. Only return `1` when you hit a node with no paths coming out of it.

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

int countLeafNodes(TreeNode* root) {
    if (!root) return 0;
    if (!root->left && !root->right) return 1;
    
    return countLeafNodes(root->left) + countLeafNodes(root->right);
}

int main() {
    // Logic...
    return 0;
}
```
