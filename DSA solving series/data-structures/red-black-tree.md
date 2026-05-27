# 🟥⬛ Red-Black Tree

## 1. The Objective
A Red-Black Tree is a self-balancing BST that uses a "color" property (Red or Black) for each node to ensure the tree remains approximately balanced. It is the underlying data structure for many standard libraries (e.g., `std::map` and `std::set` in C++).

---

## 2. Visual Logic
### The 5 Rules
1. Every node is either **Red** or **Black**.
2. The **Root** is always **Black**.
3. Every **Leaf (NULL)** is **Black**.
4. If a node is **Red**, its children must be **Black** (No two consecutive Reds).
5. For each node, every path from that node to its leaf nodes contains the same number of **Black** nodes.

---

## 3. The Logic Bridge
- **The "Good-Enough" Balance:** While AVL trees are strictly balanced, Red-Black trees are "loose" but guaranteed to never be more than twice as tall as an AVL tree.
- **Speed Tradeoff:** Because the balance is less strict, Red-Black trees require fewer rotations during insertion/deletion, making them faster for dynamic data sets compared to AVL trees.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Conceptual Logic)

```cpp
/**
 * Simplified node with Color property.
 */
enum Color { RED, BLACK };

struct Node {
    int data;
    Color color;
    Node *left, *right, *parent;

    Node(int val) : data(val), color(RED), left(nullptr), right(nullptr), parent(nullptr) {}
};

// Balancing usually involves 'Re-coloring' and 'Rotations'.
// std::map and std::set use this internally.
```

---
[➔ Back to Tree Hub](tree.md) | [➔ Back to Roadmap](../DSA-Master-Roadmap.md)
