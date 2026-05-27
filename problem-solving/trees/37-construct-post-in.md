# 37 | Construct Tree from Post-order & In-order

Rebuild a tree using post-traversal data.

---

## 1. The Objective
Same as Problem 36, but using Post-order.

---

## 2. Visual Logic
The **last** element in Post-order is the Root. Rebuild by scanning Post-order from back to front.

---

## 3. The "Aha!" Moment
When rebuilding from the back of Post-order, you must build the **Right Subtree first**, then the Left.

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

TreeNode* build(std::vector<int>& post, int& pIdx, int inStart, int inEnd, auto& m) {
    if (inStart > inEnd) return nullptr;
    
    TreeNode* root = new TreeNode(post[pIdx--]);
    int split = m[root->val];
    
    root->right = build(post, pIdx, split + 1, inEnd, m); // Right first!
    root->left = build(post, pIdx, inStart, split - 1, m);
    return root;
}
```
