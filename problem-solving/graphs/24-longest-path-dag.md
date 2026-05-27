# 24 | Longest Path in a DAG

Find the maximum distance in an acyclic directed graph.

---

## 1. The Objective
Shortest path is easy (BFS). Longest path is usually NP-Hard, but in a **DAG**, it's solvable in $O(V+E)$.

---

## 2. Visual Logic
### The "Topo-DP" Strategy
1. Find topological order.
2. Initialize `dist[V] = -inf`.
3. Process nodes in topological order:
   - For each neighbor $V$ of $U$:
     - `dist[V] = max(dist[V], dist[U] + weight_UV)`

---

## 3. The "Aha!" Moment
Because there are no cycles, you can "safely" build up your path length without worrying about infinite loops.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
#include <climits>

void findLongest(const std::vector<std::vector<std::pair<int, int>>>& adj) {
    // 1. Get Topo Order (see Prob 21)
    // 2. dist[V] = 0 (or -inf)
    // 3. Update neighbors
}
```
*(Implementation omitted for brevity, logic described)*
