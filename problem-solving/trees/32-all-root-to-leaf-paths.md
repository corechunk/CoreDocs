# 32 | All Root-to-Leaf Paths

Print every unique path from the top to every leaf.

---

## 1. The Objective
Given a tree, output strings like `"1->2->4"`.

---

## 2. Visual Logic
### The "Backtracking" Path
1. Maintain a current `path` vector.
2. Add Root to `path`.
3. If leaf, print `path`.
4. Go Left, then Right.
5. **CRITICAL:** Pop Root from `path` before returning (undo the choice).

---

## 3. The "Aha!" Moment
Backtracking ensures that when the recursion "climbs back up," it cleans up its trail so it doesn't leak into other paths.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <string>

struct TreeNode {
    int val;
    TreeNode *left, *right;
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
};

void findPaths(TreeNode* root, std::string path, std::vector<std::string>& res) {
    if (!root) return;
    
    path += std::to_string(root->val);
    if (!root->left && !root->right) {
        res.push_back(path);
    } else {
        path += "->";
        findPaths(root->left, path, res);
        findPaths(root->right, path, res);
    }
}
```
