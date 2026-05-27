# 22 | Topological Sort (Kahn's Algorithm)

The iterative (BFS-style) way to perform topological sorting.

---

## 1. The Objective
Order nodes by resolving zero-dependency nodes first.

---

## 2. Visual Logic
### The "In-degree Zero" Strategy
1. Calculate In-degree of all nodes.
2. Put all nodes with `in-degree == 0` into a Queue.
3. While Queue is not empty:
   - Pop node $U$. Add to result.
   - For each neighbor $V$ of $U$:
     - Decrement in-degree of $V$.
     - If `in-degree[V] == 0`: Push $V$ to Queue.

---

## 3. The "Aha!" Moment
If the result list is smaller than the total nodes, there must be a cycle (the algorithm got stuck). This is an iterative way to detect cycles!

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <queue>

void kahnsSort(const std::vector<std::vector<int>>& adj) {
    int V = adj.size();
    std::vector<int> inDegree(V, 0);
    for (int i = 0; i < V; i++) for (int v : adj[i]) inDegree[v]++;
    
    std::queue<int> q;
    for (int i = 0; i < V; i++) if (inDegree[i] == 0) q.push(i);
    
    while (!q.empty()) {
        int u = q.front(); q.pop();
        std::cout << u << " ";
        for (int v : adj[u]) {
            if (--inDegree[v] == 0) q.push(v);
        }
    }
}
```
