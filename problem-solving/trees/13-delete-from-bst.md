# 13 | Delete from BST

Remove a node and restructure the tree.

---

## 1. The Objective
Handle 3 cases of deletion:
1. **Leaf:** Just delete.
2. **One Child:** Replace node with child.
3. **Two Children:** Replace with **In-order Successor** (smallest in right subtree) and delete that successor.

---

## 2. Visual Logic
### Case 3: The "Promotion"
To delete a parent with two kids:
1. Find the smallest kid on the Right.
2. Put its value in the parent's spot.
3. Delete the duplicate kid.

---

## 3. The "Aha!" Moment
The In-order Successor is guaranteed to have at most one child, making it easy to delete after the swap.

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

TreeNode* findMin(TreeNode* root) {
    while (root && root->left) root = root->left;
    return root;
}

TreeNode* deleteNode(TreeNode* root, int key) {
    if (!root) return root;
    
    if (key < root->val) root->left = deleteNode(root->left, key);
    else if (key > root->val) root->right = deleteNode(root->right, key);
    else {
        // Case 1 & 2
        if (!root->left) { TreeNode* temp = root->right; delete root; return temp; }
        if (!root->right) { TreeNode* temp = root->left; delete root; return temp; }
        
        // Case 3
        TreeNode* temp = findMin(root->right);
        root->val = temp->val;
        root->right = deleteNode(root->right, temp->val);
    }
    return root;
}
```
