# 20 | K-Cores of a Graph

Find a subgraph where each node has a degree at least $K$.

---

## 1. The Objective
Delete nodes that don't meet the "friendship" requirement until everyone remaining has at least $K$ connections.

---

## 2. Visual Logic
### The "Recursive Pruning"
1. Calculate degree of all nodes.
2. If any node has `degree < K`:
   - Delete it.
   - Decrement the degree of all its neighbors.
   - If any neighbor now has `degree < K`, repeat for that neighbor.

---

## 3. The "Aha!" Moment
This is like social filtration. If you remove the loners, it might make their few friends also become loners, causing a chain reaction of removals.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

bool prune(int u, int k, std::vector<int>& deg, const std::vector<std::vector<int>>& adj, std::vector<bool>& deleted) {
    if (deg[u] < k) {
        deleted[u] = true;
        for (int v : adj[u]) {
            if (!deleted[v]) {
                deg[v]--;
                prune(v, k, deg, adj, deleted);
            }
        }
        return true;
    }
    return false;
}

void kCores(const std::vector<std::vector<int>>& adj, int k) {
    int V = adj.size();
    std::vector<int> deg(V);
    std::vector<bool> deleted(V, false);
    for(int i=0; i<V; i++) deg[i] = adj[i].size();
    
    for(int i=0; i<V; i++) prune(i, k, deg, adj, deleted);
    // Print non-deleted...
}
```
