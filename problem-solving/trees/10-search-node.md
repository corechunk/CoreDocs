# 10 | Search for a Node

Find if a value `X` exists in a standard Binary Tree.

---

## 1. The Objective
Return true if target is found, else false.

---

## 2. Visual Logic
Recursive "OR" search:
- Am I the target? OR
- Is it in my Left? OR
- Is it in my Right?

---

## 3. The "Aha!" Moment
In an unsorted tree, this is $O(n)$ because you might have to check every single node.

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

bool search(TreeNode* root, int x) {
    if (!root) return false;
    if (root->val == x) return true;
    
    return search(root->left, x) || search(root->right, x);
}

int main() {
    // Logic...
    return 0;
}
```
