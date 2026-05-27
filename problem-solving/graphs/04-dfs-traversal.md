# 04 | DFS Traversal (Graphs)

Explore as deep as possible along each branch before backtracking.

---

## 1. The Objective
Visit every reachable node by diving into its neighbors recursively.

---

## 2. Visual Logic
### The "Labyrinth" Strategy
1. Mark current node as **Visited**.
2. For each neighbor:
   - If not visited: Recurse into it.

---

## 3. The "Aha!" Moment
DFS is the natural way to solve connectivity problems, finding components, and topological sorting. It uses the function call stack (LIFO) instead of a queue.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

void dfsUtil(int u, const std::vector<std::vector<int>>& adj, std::vector<bool>& visited) {
    visited[u] = true;
    std::cout << u << " ";

    for (int v : adj[u]) {
        if (!visited[v]) {
            dfsUtil(v, adj, visited);
        }
    }
}

void dfs(int start, const std::vector<std::vector<int>>& adj) {
    std::vector<bool> visited(adj.size(), false);
    dfsUtil(start, adj, visited);
}
```
