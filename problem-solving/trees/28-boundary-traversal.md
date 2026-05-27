# 28 | Boundary Traversal

Print the nodes on the outer edges in anti-clockwise order.

---

## 1. The Objective
1. Print **Root**.
2. Print **Left Boundary** (excluding leaf).
3. Print all **Leaf Nodes**.
4. Print **Right Boundary** (excluding leaf, in reverse).

---

## 2. Visual Logic
Think of it like gift-wrapping the tree. You start at the top, slide down the left, walk across the bottom floor, and climb up the right.

---

## 3. The "Aha!" Moment
This is three separate problems solved in sequence. You must be careful to avoid printing the same node (like the leftmost leaf) twice.

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

void leftB(TreeNode* root) {
    if (!root || (!root->left && !root->right)) return;
    std::cout << root->val << " ";
    if (root->left) leftB(root->left);
    else leftB(root->right);
}

void leaves(TreeNode* root) {
    if (!root) return;
    if (!root->left && !root->right) std::cout << root->val << " ";
    leaves(root->left);
    leaves(root->right);
}

void rightB(TreeNode* root) {
    if (!root || (!root->left && !root->right)) return;
    if (root->right) rightB(root->right);
    else rightB(root->left);
    std::cout << root->val << " "; // Print after recursion (Reverse)
}
```
