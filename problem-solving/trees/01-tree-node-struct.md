# 01 | TreeNode Struct

Define the fundamental building block of a Binary Tree.

---

## 1. The Objective
Create a structure in C++ that can store a value and point to two child nodes (Left and Right).

---

## 2. Visual Logic
### The "Recursive Node"
Each node contains:
1. **Data:** The value (int, string, etc.).
2. **Left Pointer:** Link to the left subtree.
3. **Right Pointer:** Link to the right subtree.

```text
       [ Data ]
       /      \
  [ Left* ]  [ Right* ]
```

---

## 3. The "Aha!" Moment
A tree is a recursive structure. Each child pointer points to something that is itself a `TreeNode`. This self-referential pointer is why we use `TreeNode*`.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy: Standard Recursive Struct
 */
struct TreeNode {
    int val;
    TreeNode *left;
    TreeNode *right;
    
    // Constructor for easy initialization
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
};

int main() {
    // Manually creating a small tree
    //     1
    //    / \
    //   2   3
    TreeNode* root = new TreeNode(1);
    root->left = new TreeNode(2);
    root->right = new TreeNode(3);
    
    std::cout << "Root: " << root->val << std::endl;
    std::cout << "Left: " << root->left->val << std::endl;
    
    return 0;
}
```
