# 11 | Count Connected Components

Determine how many disconnected subgraphs exist.

---

## 1. The Objective
Identify separate "islands" of nodes.

---

## 2. Visual Logic
### The "Forest" Strategy
1. Loop through every node $i$ from 0 to $V-1$:
2. If $i$ has not been visited:
   - Increment `componentCount`.
   - Start a DFS/BFS from $i$ to mark its entire island as visited.

---

## 3. The "Aha!" Moment
The number of times you have to "kick-start" a traversal is exactly the number of components.

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

int countComponents(const std::vector<std::vector<int>>& adj) {
    int count = 0;
    std::vector<bool> visited(adj.size(), false);
    for (int i = 0; i < adj.size(); i++) {
        if (!visited[i]) {
            count++;
            dfs(i, adj, visited);
        }
    }
    return count;
}
```
