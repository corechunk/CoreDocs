# 10 | Check if Graph is Connected

Verify if every node can reach every other node.

---

## 1. The Objective
For an undirected graph, check if it consists of exactly one connected component.

---

## 2. Visual Logic
1. Start a traversal from node 0.
2. Count how many nodes were visited.
3. If `visitedCount == TotalNodes`, the graph is connected.

---

## 3. The "Aha!" Moment
If any node is left "un-visited" after a full traversal starting from the root, there must be a gap in the network.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

void dfs(int u, const std::vector<std::vector<int>>& adj, std::vector<bool>& visited) {
    visited[u] = true;
    for (int v : adj[u]) if (!visited[v]) dfs(v, adj, visited);
}

bool isConnected(const std::vector<std::vector<int>>& adj) {
    if (adj.empty()) return true;
    std::vector<bool> visited(adj.size(), false);
    
    dfs(0, adj, visited);
    
    for (bool v : visited) if (!v) return false;
    return true;
}
```
