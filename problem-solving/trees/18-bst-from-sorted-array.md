# 18 | BST from Sorted Array

Construct a height-balanced BST from a sorted array.

---

## 1. The Objective
Given `[1, 2, 3, 4, 5, 6, 7]`, create a tree that is not skewed.

---

## 2. Visual Logic
### The "Middle is Root" Strategy
1. Pick the middle element as Root.
2. Recursive call for Left half of array.
3. Recursive call for Right half.

```text
[1, 2, 3, 4, 5, 6, 7]
Mid = 4 (ROOT)
Left half: [1, 2, 3] -> Mid = 2 (Left Child)
Right half: [5, 6, 7] -> Mid = 6 (Right Child)
```

---

## 3. The "Aha!" Moment
By always picking the middle, you ensure the number of nodes on the left and right differ by at most 1.

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

TreeNode* sortedArrayToBST(std::vector<int>& nums, int start, int end) {
    if (start > end) return nullptr;
    
    int mid = start + (end - start) / 2;
    TreeNode* root = new TreeNode(nums[mid]);
    
    root->left = sortedArrayToBST(nums, start, mid - 1);
    root->right = sortedArrayToBST(nums, mid + 1, end);
    
    return root;
}
```
