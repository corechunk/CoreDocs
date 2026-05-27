# 03 | BFS Traversal (Graphs)

Visit nodes level by level using a queue.

---

## 1. The Objective
Explore the graph starting from source `S`, visiting all reachable nodes level-by-level.

---

## 2. Visual Logic
### The "Ripple" Effect
1. Put **Start** in a Queue, mark as **Visited**.
2. While Queue is not empty:
   - Pop node $U$.
   - For every neighbor $V$ of $U$:
     - If not visited: Add to Queue, mark as Visited.

---

## 3. The "Aha!" Moment
BFS is the engine for finding the **Shortest Path** in an unweighted graph. It always finds a node's distance in terms of "minimum hops" from the source.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <queue>

void bfs(int start, const std::vector<std::vector<int>>& adj) {
    int V = adj.size();
    std::vector<bool> visited(V, false);
    std::queue<int> q;

    visited[start] = true;
    q.push(start);

    while (!q.empty()) {
        int u = q.front(); q.pop();
        std::cout << u << " ";

        for (int v : adj[u]) {
            if (!visited[v]) {
                visited[v] = true;
                q.push(v);
            }
        }
    }
}
```
