# 31 | Dijkstra's Algorithm

Find the shortest path in a weighted graph (no negative weights).

---

## 1. The Objective
Given source $S$, find the minimum cost to reach all other nodes.

---

## 2. Visual Logic
### The "Greedy Expansion"
1. Initialize `dist[S] = 0`, all others `inf`.
2. Use a **Priority Queue** to always pick the "nearest" unvisited node.
3. For each neighbor $V$ of current node $U$:
   - If `dist[U] + weight_UV < dist[V]`: Update `dist[V]` and push to PQ.

---

## 3. The "Aha!" Moment
Dijkstra's is essentially BFS with a "Cost" instead of a "Hop count." The Priority Queue ensures we always process the truly shortest path first.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <queue>
#include <climits>

void dijkstra(int start, const std::vector<std::vector<std::pair<int, int>>>& adj) {
    int V = adj.size();
    std::vector<int> dist(V, INT_MAX);
    std::priority_queue<std::pair<int, int>, std::vector<std::pair<int, int>>, std::greater<std::pair<int, int>>> pq;

    dist[start] = 0;
    pq.push({0, start});

    while (!pq.empty()) {
        int d = pq.top().first;
        int u = pq.top().second;
        pq.pop();

        if (d > dist[u]) continue;

        for (auto edge : adj[u]) {
            int v = edge.first, w = edge.second;
            if (dist[u] + w < dist[v]) {
                dist[v] = dist[u] + w;
                pq.push({dist[v], v});
            }
        }
    }
}
```
