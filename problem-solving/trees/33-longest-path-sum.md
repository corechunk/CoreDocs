# 33 | Longest Path Sum

Find the maximum sum of values along any root-to-leaf path.

---

## 1. The Objective
Return the sum of the "Heaviest" path.

---

## 2. Visual Logic
Sum = `root->val + max(maxPath(left), maxPath(right))`.

---

## 3. The "Aha!" Moment
This combines the logic of "Find Height" (finding the longest path) and "Sum of Nodes."

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

int maxPathSumRootToLeaf(TreeNode* root) {
    if (!root) return 0;
    return root->val + std::max(maxPathSumRootToLeaf(root->left), 
                                maxPathSumRootToLeaf(root->right));
}
```
