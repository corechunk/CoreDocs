# 18 | Transitive Closure

Compute a reachability matrix for the graph.

---

## 1. The Objective
Build a $V \times V$ matrix where `res[i][j] = 1` if a path exists from $i$ to $j$.

---

## 2. Visual Logic
Perform a DFS from **every** node. Mark reachable nodes in the corresponding row of the result matrix.

---

## 3. The "Aha!" Moment
This essentially pre-calculates the answer to every possible "Check if Path Exists" (Problem 07) query.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

void reachDFS(int u, int v, std::vector<std::vector<int>>& res, const std::vector<std::vector<int>>& adj) {
    res[u][v] = 1;
    for (int neighbor : adj[v]) {
        if (!res[u][neighbor]) {
            reachDFS(u, neighbor, res, adj);
        }
    }
}

void transitiveClosure(const std::vector<std::vector<int>>& adj) {
    int V = adj.size();
    std::vector<std::vector<int>> res(V, std::vector<int>(V, 0));
    for (int i = 0; i < V; i++) reachDFS(i, i, res, adj);
    // Print...
}
```
