# 31 | Path Sum Exists

Check if there is a root-to-leaf path that sums to $K$.

---

## 1. The Objective
Given `K=22`, find if any path from top to bottom adds up to 22.

---

## 2. Visual Logic
### The "Subtraction" Strategy
1. Start at Root with `needed = K`.
2. Subtract current value: `needed = needed - root->val`.
3. If at leaf and `needed == 0`, success!
4. Otherwise, ask Left and Right if they can find the new `needed` sum.

---

## 3. The "Aha!" Moment
You don't need an accumulator. By subtracting, you simplify the problem at every level until it becomes "Find sum 0 in the remaining subtrees."

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

bool hasPathSum(TreeNode* root, int sum) {
    if (!root) return false;
    
    // Check if leaf
    if (!root->left && !root->right) {
        return sum == root->val;
    }
    
    return hasPathSum(root->left, sum - root->val) || 
           hasPathSum(root->right, sum - root->val);
}
```
