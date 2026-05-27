# 16 | Shortest Path (Unweighted)

Find the minimum number of edges to get from A to B.

---

## 1. The Objective
Given an unweighted graph, find the hop-count of the shortest path.

---

## 2. Visual Logic
### The "Step Counter" BFS
1. Use BFS.
2. Store `distance[V] = distance[U] + 1` when discovering a new node.

---

## 3. The "Aha!" Moment
In BFS, the first time you "touch" a node, you have found the fastest way to get there.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <queue>

int shortestPath(int start, int target, const std::vector<std::vector<int>>& adj) {
    std::vector<int> dist(adj.size(), -1);
    std::queue<int> q;
    
    dist[start] = 0;
    q.push(start);
    
    while (!q.empty()) {
        int u = q.front(); q.pop();
        if (u == target) return dist[u];
        
        for (int v : adj[u]) {
            if (dist[v] == -1) {
                dist[v] = dist[u] + 1;
                q.push(v);
            }
        }
    }
    return -1;
}
```
