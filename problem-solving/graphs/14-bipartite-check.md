# 14 | Bipartite Check

Check if a graph can be colored with only two colors such that no two adjacent nodes have the same color.

---

## 1. The Objective
Can you split the nodes into two independent sets?

---

## 2. Visual Logic
### The "Alternating Color" Strategy
1. Color Root: **Red**.
2. Color all Neighbors: **Blue**.
3. Color Neighbors of Neighbors: **Red**.
If you ever try to color a node with its neighbor's color, the graph is NOT bipartite.

---

## 3. The "Aha!" Moment
A graph is Bipartite if and only if it has **No Odd Cycles**.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <queue>

bool isBipartite(const std::vector<std::vector<int>>& adj) {
    int V = adj.size();
    std::vector<int> color(V, -1); // -1: uncolored, 0: Red, 1: Blue
    
    for (int i = 0; i < V; i++) {
        if (color[i] == -1) {
            std::queue<int> q;
            q.push(i); color[i] = 0;
            while (!q.empty()) {
                int u = q.front(); q.pop();
                for (int v : adj[u]) {
                    if (color[v] == -1) {
                        color[v] = 1 - color[u];
                        q.push(v);
                    } else if (color[v] == color[u]) return false;
                }
            }
        }
    }
    return true;
}
```
