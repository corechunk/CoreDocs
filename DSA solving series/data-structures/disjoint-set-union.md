# 🤝 Disjoint Set Union (DSU / Union-Find)

## 1. The Objective
DSU is a data structure that tracks a set of elements partitioned into a number of **disjoint (non-overlapping) subsets**. It provides two near-instant operations:
1. **Find:** Determine which subset an element is in.
2. **Union:** Join two subsets into a single subset.

---

## 2. Visual Logic
### Representative Nodes
Elements are represented as trees. The **Root** of the tree is the "ID" of the set.
```text
Set A: [1] <- [2]    Set B: [3] <- [4]
        ^                    ^
      Root                 Root
```
- `Find(2)` returns `1`.
- `Union(1, 3)` makes one root point to the other.

---

## 3. The Logic Bridge
- **Path Compression:** Every time we call `Find(x)`, we make every node on the path point **directly to the root**. This flattens the tree, making future calls $O(1)$.
- **Union by Rank/Size:** We always attach the smaller tree under the larger tree to keep the height minimal.
- **Amortized Near-Constant:** With both optimizations, DSU operations take **$\alpha(n)$** time, where $\alpha$ is the Inverse Ackermann function (effectively constant for all practical values of $N$).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Optimized DSU)

```cpp
#include <iostream>
#include <vector>

class DSU {
    std::vector<int> parent;
public:
    DSU(int n) {
        parent.resize(n + 1);
        for (int i = 1; i <= n; i++) parent[i] = i;
    }

    // Find with Path Compression
    int find(int i) {
        if (parent[i] == i) return i;
        return parent[i] = find(parent[i]);
    }

    // Simple Union
    void unite(int i, int j) {
        int root_i = find(i);
        int root_j = find(j);
        if (root_i != root_j) parent[root_i] = root_j;
    }
};

int main() {
    DSU dsu(5);
    dsu.unite(1, 2);
    dsu.unite(2, 3);
    std::cout << "1 and 3 connected: " << (dsu.find(1) == dsu.find(3)) << std::endl;
    return 0;
}
```

---
[➔ Back to Roadmap](../DSA-Master-Roadmap.md)
