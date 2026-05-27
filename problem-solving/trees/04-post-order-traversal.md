# 04 | Post-order Traversal

Visit nodes in the order: **Left $\to$ Right $\to$ Root**.

---

## 1. The Objective
Visit children before parents (useful for deleting trees or calculating sizes).

---

## 2. Visual Logic
### The "Bottom-Up" Scan
```text
      1
     / \
    2   3
```
Order: **2, 3, 1**

---

## 3. The "Aha!" Moment
Post-order is used when you need to know the result of children (like their height or total sum) **before** you can calculate the result for the parent.

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

/**
 * Strategy: Recursive Post-order
 */
void postOrder(TreeNode* root) {
    if (!root) return;
    
    postOrder(root->left);
    postOrder(root->right);
    std::cout << root->val << " ";
}

int main() {
    // Logic...
    return 0;
}
```
