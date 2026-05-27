# 🌲 Minimum Spanning Tree (MST)

## 1. The Objective
A Minimum Spanning Tree is a subset of the edges of a connected, edge-weighted graph that connects all the vertices together, **without any cycles**, and with the **minimum possible total edge weight**. It is used in **Cable Layouts**, **Network Design**, and **Circuit Board Routing**.

---

## 2. Visual Logic
### The Spanning Property
```text
Original Graph:       Possible MST:
(A)-2-(B)-1-(C)       (A)-2-(B)-1-(C)
 |    /               (Total Weight: 3)
 4   3
 | /
(D)
```
- All nodes (A, B, C, D) are reachable.
- No loops.
- Total sum of edge weights is minimized.

---

## 3. The Logic Bridge
- **The "Cut" Property:** For any cut of the graph (partitioning vertices into two sets), the smallest edge crossing the cut must be part of the MST.
- **Kruskal's vs. Prim's:**
    - **Kruskal's:** Focuses on **Edges**. Sorts all edges and adds them if they don't form a cycle (Global approach).
    - **Prim's:** Focuses on **Vertices**. Grows the tree from a starting node by always picking the cheapest neighbor (Local expansion).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Edge Sorting)

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

struct Edge {
    int u, v, weight;
    bool operator<(const Edge& other) const {
        return weight < other.weight;
    }
};

int main() {
    std::vector<Edge> edges = {{0, 1, 10}, {0, 2, 6}, {0, 3, 5}, {1, 3, 15}, {2, 3, 4}};
    std::sort(edges.begin(), edges.end());

    std::cout << "Cheapest edge: " << edges[0].u << " - " << edges[0].v << " (" << edges[0].weight << ")" << std::endl;
    return 0;
}
```

---

## 🔗 Sub-Topics (Specific MST Strategies)
- [Kruskal's Algorithm](kruskal.md) - Edge-based (Uses DSU).
- [Prim's Algorithm](prim.md) - vertex-based (Uses Priority Queue).

[➔ Back to Roadmap](../DSA-Master-Roadmap.md)
