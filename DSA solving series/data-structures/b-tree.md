# 🗄️ B-Trees & LSM Trees

## 1. The Objective
B-Trees and Log-Structured Merge (LSM) Trees are specialized data structures designed for **Storage Systems** (Hard Drives, SSDs, Databases). They optimize for reading and writing large blocks of data while minimizing disk seeks.

---

## 2. Visual Logic
### B-Tree (Multi-way Search Tree)
Unlike a binary tree (2 children), a B-Tree node can have hundreds of children.
```text
      [ 10 | 20 | 30 ]  <-- Node with multiple keys
     /     |     |     \
  [...]  [...]  [...]  [...]
```

### LSM Tree (Write-Optimized)
- **MemTable:** In-memory sorted tree (fast writes).
- **SSTables:** On-disk sorted files (efficient reads via compaction).

---

## 3. The Logic Bridge
- **Disk Latency:** Accessing RAM is nano-seconds; accessing disk is milliseconds (millions of times slower). 
- **Page Efficiency:** B-Trees are wide and shallow. This means even for billions of records, we only need 3-4 disk reads to find any item. Binary trees would be too deep ($O(\log_2 N)$ vs $O(\log_{100} N)$).
- **Sequential Power:** LSM Trees turn random writes into sequential writes, which is significantly faster on modern SSDs.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Abstract B-Tree Node)

```cpp
#include <iostream>
#include <vector>

/**
 * A B-Tree node for degree M.
 */
template <int M>
struct BTreeNode {
    std::vector<int> keys;
    std::vector<BTreeNode*> children;
    bool isLeaf;

    BTreeNode(bool leaf) : isLeaf(leaf) {
        keys.reserve(M - 1);
        children.reserve(M);
    }
};

// Internal logic involves 'Splitting' nodes when they exceed M-1 keys.
```

---
[➔ Back to Tree Hub](tree.md) | [➔ Back to Roadmap](../DSA-Master-Roadmap.md)
