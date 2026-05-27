# 🌳 Trees (Hierarchical Depth)

## 1. The Objective
A Tree is a non-linear data structure that represents a hierarchical relationship between "nodes". Unlike linear structures (Arrays, Linked Lists) which have a single logical "next" element, a tree node can point to multiple "children", forming a branching structure that originates from a single **Root**.

---

## 2. Visual Logic
### The Anatomy of a Tree
```text
          [Root]          <-- Level 0
         /      \
      [Node]   [Node]     <-- Level 1 (Children of Root)
      /    \       \
   [Leaf] [Leaf]  [Leaf]  <-- Level 2 (Nodes with no children)
```

### Key Metrics
- **Height:** The longest path from a node to a leaf (Root height is the tree height).
- **Depth:** The path length from the root to a specific node.

---

## 3. The "Aha!" Moment
- **Non-Linearity:** Trees are the natural way to represent hierarchies (File systems, DOM trees, Organizational charts).
- **Efficiency:** By organizing data hierarchically (like in a BST), we can reduce $O(n)$ linear searches to $O(\log n)$ by discarding half of the possibilities at every step.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Generic Node)

```cpp
#include <iostream>
#include <vector>

/**
 * A Generic Tree Node that can have N children.
 */
struct TreeNode {
    int data;
    std::vector<TreeNode*> children;

    TreeNode(int val) : data(val) {}
};

void printTree(TreeNode* root, int depth = 0) {
    if (!root) return;
    for (int i = 0; i < depth; i++) std::cout << "  ";
    std::cout << "|-- " << root->data << std::endl;
    for (auto child : root->children) {
        printTree(child, depth + 1);
    }
}

int main() {
    TreeNode* root = new TreeNode(1);
    root->children.push_back(new TreeNode(2));
    root->children.push_back(new TreeNode(3));
    root->children[0]->children.push_back(new TreeNode(4));

    std::cout << "General Tree Structure:" << std::endl;
    printTree(root);
    return 0;
}
```

---

## 🔗 Sub-Topics (Specific Tree Types)
- [Binary Tree](binary-tree.md) - Nodes with max 2 children.
- [Binary Search Tree (BST)](bst.md) - Sorted binary tree.
- [AVL Tree](avl-tree.md) - Self-balancing BST (Height-based).
- [Red-Black Tree](red-black-tree.md) - Self-balancing BST (Color-based).
- [B-Tree & LSM Tree](b-tree.md) - Multi-way trees for DBs.
- [Trie (Prefix Tree)](trie.md) - String-based search trees.
- [Segment Tree](segment-tree.md) - Range query optimization.
- [Fenwick Tree](fenwick-tree.md) - Binary Indexed Tree for prefix sums.

[➔ Back to Roadmap](../DSA-Master-Roadmap.md)
