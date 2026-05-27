# 15 | Flood Fill (Graph Version)

Visit all nodes in the same "cluster".

---

## 1. The Objective
Basically Problem 05 (Count Nodes), but specifically focused on labeling/marking a component.

---

## 2. Visual Logic
Same as Tree/Grid flood fill, but navigating via Adjacency List.

---

## 3. The "Aha!" Moment
Flood fill is just "DFS with a task." It represents how viruses spread or how data propogates through a network.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

void floodMark(int u, int color, std::vector<int>& marker, const std::vector<std::vector<int>>& adj) {
    marker[u] = color;
    for (int v : adj[u]) {
        if (marker[v] == 0) {
            floodMark(v, color, marker, adj);
        }
    }
}
```
