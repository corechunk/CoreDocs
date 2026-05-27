# 19 | Mother Vertex

Find a node that can reach all other nodes in the graph.

---

## 1. The Objective
Identify a "Source" node for the entire directed graph.

---

## 2. Visual Logic
### The "Last Finisher" Strategy
1. Perform DFS. Keep track of the last node that finished its processing. Let's call it `v`.
2. Perform a **second** DFS starting only from `v`.
3. If this second DFS visits all nodes, `v` is a Mother Vertex.

---

## 3. The "Aha!" Moment
If a Mother Vertex exists, it must be the last node finished in a standard DFS traversal. This is similar to the logic used in finding Strongly Connected Components.

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

int findMother(const std::vector<std::vector<int>>& adj) {
    int V = adj.size();
    std::vector<bool> visited(V, false);
    int lastV = 0;
    
    for (int i = 0; i < V; i++) {
        if (!visited[i]) {
            dfs(i, adj, visited);
            lastV = i;
        }
    }
    
    std::fill(visited.begin(), visited.end(), false);
    dfs(lastV, adj, visited);
    for (bool v : visited) if (!v) return -1;
    return lastV;
}
```
