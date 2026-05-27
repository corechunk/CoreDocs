# 36 | Construct Tree from Pre-order & In-order

Rebuild a unique Binary Tree from its traversal sequences.

---

## 1. The Objective
Given `pre = [3, 9, 20]`, `in = [9, 3, 20]`, rebuild the tree.

---

## 2. Visual Logic
### The "Split Point" Strategy
1. The **first** element in Pre-order is always the **Root** (3).
2. Find (3) in the In-order list.
3. Everything to the **Left** of (3) in In-order is the Left Subtree.
4. Everything to the **Right** of (3) in In-order is the Right Subtree.
5. Recurse.

---

## 3. The "Aha!" Moment
Pre-order tells you **Who** is the parent. In-order tells you **Where** the children are. Together, they define a unique structure.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <unordered_map>

struct TreeNode {
    int val;
    TreeNode *left, *right;
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
};

TreeNode* build(std::vector<int>& pre, int& pIdx, int inStart, int inEnd, std::unordered_map<int,int>& m) {
    if (inStart > inEnd) return nullptr;
    
    TreeNode* root = new TreeNode(pre[pIdx++]);
    int split = m[root->val];
    
    root->left = build(pre, pIdx, inStart, split - 1, m);
    root->right = build(pre, pIdx, split + 1, inEnd, m);
    return root;
}
```
