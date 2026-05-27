# 41 | Serialize & Deserialize

Convert a tree to a string and back to a tree.

---

## 1. The Objective
Store a tree structure in a flat file or database.

---

## 2. Visual Logic
### The "Null Marker"
Use a special symbol (like '#') for NULL pointers.
`1, 2, #, #, 3, 4, #, #, #`

---

## 3. The "Aha!" Moment
Pre-order traversal with NULL markers captures the exact structure. When reading back, the first available NULL always signals the end of a branch.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>
#include <sstream>

struct TreeNode {
    int val;
    TreeNode *left, *right;
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
};

void serialize(TreeNode* root, std::ostringstream& out) {
    if (!root) { out << "# "; return; }
    out << root->val << " ";
    serialize(root->left, out);
    serialize(root->right, out);
}

TreeNode* deserialize(std::istringstream& in) {
    std::string val;
    in >> val;
    if (val == "#") return nullptr;
    TreeNode* node = new TreeNode(std::stoi(val));
    node->left = deserialize(in);
    node->right = deserialize(in);
    return node;
}
```
