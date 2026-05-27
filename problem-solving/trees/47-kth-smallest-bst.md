# 47 | Kth Smallest in BST

Find the $K^{th}$ element in a sorted list without using an extra array.

---

## 1. The Objective
Return the value that would be at index $K-1$ if you printed the BST.

---

## 2. Visual Logic
### The "Counter" Strategy
Perform In-order traversal. Instead of printing, increment a counter. When `counter == K`, you found it.

---

## 3. The "Aha!" Moment
You can stop the recursion immediately after finding the $K^{th}$ element (early exit) to save time.

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

void kth(TreeNode* root, int k, int& count, int& ans) {
    if (!root || ans != -1) return;
    
    kth(root->left, k, count, ans);
    
    count++;
    if (count == k) { ans = root->val; return; }
    
    kth(root->right, k, count, ans);
}
```
