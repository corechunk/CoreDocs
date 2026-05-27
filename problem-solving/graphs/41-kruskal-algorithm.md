# 41 | Kruskal's Algorithm

Find the Minimum Spanning Tree using edge sorting.

---

## 1. The Objective
Connect all nodes with minimum total weight.

---

## 2. Visual Logic
### The "Merge" Strategy
1. Sort all edges by weight.
2. For each edge $(U, V)$:
   - If $U$ and $V$ are in different components:
     - Add edge to MST.
     - Union (merge) the components.

---

## 3. The "Aha!" Moment
Kruskal's is greedy. By always picking the smallest available edge that doesn't create a cycle, you are guaranteed to reach the minimum cost.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

struct Edge { int u, v, w; };

bool compareEdges(Edge a, Edge b) { return a.w < b.w; }

// Requires DSU (Union-Find) to work efficiently.
```
