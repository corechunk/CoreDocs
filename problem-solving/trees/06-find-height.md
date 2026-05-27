# 06 | Find Height of Tree

Calculate the maximum distance from root to a leaf.

---

## 1. The Objective
Find the number of levels in a tree.
- A single node has height 1.
- An empty tree has height 0.

---

## 2. Visual Logic
### The "Tallest Child" Rule
Height of Root = $1 + \text{max}(\text{Height of Left Child}, \text{Height of Right Child})$.

---

## 3. The "Aha!" Moment
This is a **Post-order** recursive problem. You must ask your children how tall they are before you can decide your own height.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <algorithm>

struct TreeNode {
    int val;
    TreeNode *left, *right;
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
};

/**
 * Strategy: Recursive Max Depth
 */
int getHeight(TreeNode* root) {
    if (!root) return 0;
    
    int leftH = getHeight(root->left);
    int rightH = getHeight(root->right);
    
    return 1 + std::max(leftH, rightH);
}

int main() {
    TreeNode* root = new TreeNode(1);
    root->left = new TreeNode(2);
    root->left->left = new TreeNode(4);
    std::cout << "Height: " << getHeight(root) << std::endl; // 3
    return 0;
}
```
