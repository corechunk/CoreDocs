# ⚡ Dijkstra's Algorithm

## 1. The Objective
Dijkstra's algorithm finds the shortest paths from a single source vertex to all other vertices in a weighted graph with **non-negative** edge weights.

---

## 2. Visual Logic
### Distance Relaxation
1. Initialize `dist[source] = 0`, all others = $\infty$.
2. Use a **Priority Queue** to pick the node `u` with the smallest `dist[u]`.
3. For each neighbor `v`:
   `if (dist[u] + weight(u,v) < dist[v]) update dist[v]`.

---

## 3. The Logic Bridge
- **The "Greedy" Choice:** Dijkstra assumes that once we've found the shortest path to a node (via the priority queue), no "longer" path could ever become "shorter" by adding more positive edges. This is why it fails with negative weights.
- **Efficiency:** By using a Min-Priority Queue (Min-Heap), we reduce the complexity from $O(V^2)$ to **$O(E \log V)$**.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Priority Queue)

```cpp
#include <iostream>
#include <vector>
#include <queue>

const int INF = 1e9;

void dijkstra(int start, const std::vector<std::vector<std::pair<int, int>>>& adj) {
    int n = adj.size();
    std::vector<int> dist(n, INF);
    std::priority_queue<std::pair<int, int>, std::vector<std::pair<int, int>>, std::greater<std::pair<int, int>>> pq;

    dist[start] = 0;
    pq.push({0, start});

    while (!pq.empty()) {
        int d = pq.top().first;
        int u = pq.top().second;
        pq.pop();

        if (d > dist[u]) continue;

        for (auto edge : adj[u]) {
            int v = edge.first;
            int weight = edge.second;
            if (dist[u] + weight < dist[v]) {
                dist[v] = dist[u] + weight;
                pq.push({dist[v], v});
            }
        }
    }

    for (int i = 0; i < n; i++) std::cout << "Node " << i << ": " << dist[i] << "\n";
}

int main() {
    // adj[u] = {v, weight}
    std::vector<std::vector<std::pair<int, int>>> adj = {{{1, 4}, {2, 1}}, {{2, 2}, {3, 5}}, {{3, 8}}, {}};
    dijkstra(0, adj);
    return 0;
}
```

---
[➔ Back to Shortest Paths Hub](shortest-paths.md) | [➔ Back to Roadmap](../DSA-Master-Roadmap.md)
