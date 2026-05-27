# 42 | Prim's Algorithm

Find the Minimum Spanning Tree using node expansion.

---

## 1. The Objective
Build the MST from a single starting node.

---

## 2. Visual Logic
### The "Growth" Strategy
1. Start at node 0.
2. Always pick the smallest edge that connects a "visited" node to an "unvisited" node.
3. Use a Priority Queue to pick the edge.

---

## 3. The "Aha!" Moment
Prim's is like Dijkstra's, but it only cares about the **New Edge Weight**, not the total distance from the start.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <queue>

void prim(int n, const std::vector<std::vector<std::pair<int, int>>>& adj) {
    // Priority queue of {weight, node}
}
```
