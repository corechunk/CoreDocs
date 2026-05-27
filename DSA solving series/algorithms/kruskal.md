# ⚡ Kruskal's Algorithm

## 1. The Objective
Kruskal's algorithm is a greedy algorithm that finds a Minimum Spanning Tree for a connected weighted graph. It works by adding edges in increasing order of weight, provided the edge doesn't create a cycle.

---

## 2. Visual Logic
### The Edge-by-Edge Build
1. **Sort** all edges by weight.
2. **Iterate** through sorted edges:
   - If adding the edge $(u, v)$ connects two different sets, **Add it** to the MST.
   - Else, **Discard it** (Cycle detected).

---

## 3. The Logic Bridge
- **The DSU Engine:** Kruskal's relies on the **Disjoint Set Union (DSU)** data structure to efficiently check if two vertices are already in the same component. 
- **Global Strategy:** It is a "Forest-to-Tree" approach. It starts with $V$ individual components and merges them until only one tree remains.
- **Complexity:** **$O(E \log E)$** for sorting the edges.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Kruskal's + DSU)

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

struct Edge {
    int u, v, w;
    bool operator<(const Edge& other) { return w < other.w; }
};

struct DSU {
    std::vector<int> parent;
    DSU(int n) {
        parent.resize(n);
        for(int i=0; i<n; i++) parent[i] = i;
    }
    int find(int i) {
        if (parent[i] == i) return i;
        return parent[i] = find(parent[i]);
    }
    void unite(int i, int j) {
        int root_i = find(i);
        int root_j = find(j);
        if (root_i != root_j) parent[root_i] = root_j;
    }
};

int kruskal(int n, std::vector<Edge>& edges) {
    std::sort(edges.begin(), edges.end());
    DSU dsu(n);
    int mst_weight = 0;
    for (auto e : edges) {
        if (dsu.find(e.u) != dsu.find(e.v)) {
            dsu.unite(e.u, e.v);
            mst_weight += e.w;
        }
    }
    return mst_weight;
}

int main() {
    std::vector<Edge> edges = {{0,1,10}, {0,2,6}, {0,3,5}, {1,3,15}, {2,3,4}};
    std::cout << "MST Weight: " << kruskal(4, edges) << std::endl;
    return 0;
}
```

---
[➔ Back to MST Hub](minimum-spanning-tree.md) | [➔ Back to Roadmap](../DSA-Master-Roadmap.md)
