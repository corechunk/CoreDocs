# 05 | Level-order Traversal (BFS)

Visit every node level by level, from top to bottom and left to right.

---

## 1. The Objective
Given a tree, print its nodes as they appear horizontally.

---

## 2. Visual Logic
### The "Queue" Wave
1. Put **Root** in a Queue.
2. While Queue is not empty:
   - Take out front node. Print it.
   - Put its **Children** in the back of the queue.

```text
Queue: [1] -> Pop 1. Add [2, 3].
Queue: [2, 3] -> Pop 2. Add [4, 5].
Queue: [3, 4, 5] -> Pop 3.
...
```

---

## 3. The "Aha!" Moment
Level-order is not recursive (easily). It uses a **Queue (FIFO)** to store nodes that are "next in line" to be visited. This is a Breadth-First Search (BFS).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <queue>

struct TreeNode {
    int val;
    TreeNode *left, *right;
    TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
};

/**
 * Strategy: Iterative Queue (BFS)
 * Efficiency: Time O(n), Space O(w) where w is max width
 */
void levelOrder(TreeNode* root) {
    if (!root) return;
    
    std::queue<TreeNode*> q;
    q.push(root);
    
    while (!q.empty()) {
        TreeNode* curr = q.front();
        q.pop();
        
        std::cout << curr->val << " ";
        
        if (curr->left) q.push(curr->left);
        if (curr->right) q.push(curr->right);
    }
}

int main() {
    TreeNode* root = new TreeNode(1);
    root->left = new TreeNode(2);
    root->right = new TreeNode(3);
    levelOrder(root);
    return 0;
}
```
