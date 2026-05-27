# 43 | DSU (Union-Find) Basics

Maintain and merge sets of nodes efficiently.

---

## 1. The Objective
Quickly answer: "Are A and B in the same set?" and "Merge the sets of A and B."

---

## 2. Visual Logic
### The "Family Tree"
Each node points to a `parent`.
- `find(X)`: Follow pointers to find the "Leader" of the set.
- `union(A, B)`: Make the leader of A point to the leader of B.

---

## 3. The "Aha!" Moment
This is the specialized structure for connectivity without using DFS/BFS. It’s $O(\alpha(n))$, which is effectively constant time.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

class DSU {
    std::vector<int> parent;
public:
    DSU(int n) {
        parent.resize(n);
        for(int i=0; i<n; i++) parent[i] = i;
    }
    int find(int i) {
        if (parent[i] == i) return i;
        return find(parent[i]);
    }
    void unite(int i, int j) {
        int root_i = find(i), root_j = find(j);
        if (root_i != root_j) parent[root_i] = root_j;
    }
};
```
