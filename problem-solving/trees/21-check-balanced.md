# 21 | Check if Balanced (AVL Condition)

Determine if the heights of two subtrees of any node differ by no more than 1.

---

## 1. The Objective
A tree is height-balanced if for every node, `abs(height(left) - height(right)) <= 1`.

---

## 2. Visual Logic
### The "Height Signal"
1. Calculate height of left.
2. Calculate height of right.
3. If difference $> 1$, return a special "Error" value (like -1) to signal unbalance upwards.

---

## 3. The "Aha!" Moment
Don't call `getHeight()` separately for every node ($O(n^2)$). Instead, integrate the balance check into the height calculation ($O(n)$).

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

int check(TreeNode* root) {
    if (!root) return 0;
    
    int lh = check(root->left);
    if (lh == -1) return -1;
    
    int rh = check(root->right);
    if (rh == -1) return -1;
    
    if (std::abs(lh - rh) > 1) return -1;
    return 1 + std::max(lh, rh);
}

bool isBalanced(TreeNode* root) {
    return check(root) != -1;
}
```
