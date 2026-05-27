# 🔔 Bellman-Ford Algorithm

## 1. The Objective
The Bellman-Ford algorithm finds the shortest paths from a single source vertex to all other vertices in a weighted graph. Unlike Dijkstra, it can handle **negative edge weights** and detect **negative cycles**.

---

## 2. Visual Logic
### Edge Relaxation
For a graph with $V$ vertices, we relax **all edges** exactly **$V-1$** times.
```text
1. dist[source] = 0, others = INF
2. Repeat V-1 times:
   For each edge (u, v) with weight w:
     if (dist[u] + w < dist[v]) dist[v] = dist[u] + w
```

---

## 3. The Logic Bridge
- **The $V-1$ Limit:** The longest possible shortest path in a graph with $V$ nodes has at most $V-1$ edges. By relaxing $V-1$ times, we guarantee that we've found the shortest path.
- **Negative Cycle Detection:** If we relax a **V-th** time and a distance still decreases, it means a negative cycle exists (a loop where you can reduce distance infinitely).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

struct Edge {
    int u, v, w;
};

void bellmanFord(int n, int start, std::vector<Edge>& edges) {
    std::vector<int> dist(n, 1e9);
    dist[start] = 0;

    for (int i = 0; i < n - 1; i++) {
        for (auto e : edges) {
            if (dist[e.u] != 1e9 && dist[e.u] + e.w < dist[e.v])
                dist[e.v] = dist[e.u] + e.w;
        }
    }

    // Negative cycle check
    for (auto e : edges) {
        if (dist[e.u] != 1e9 && dist[e.u] + e.w < dist[e.v]) {
            std::cout << "Negative cycle detected!\n";
            return;
        }
    }

    for (int i = 0; i < n; i++) std::cout << "Node " << i << ": " << dist[i] << "\n";
}

int main() {
    std::vector<Edge> edges = {{0, 1, -1}, {0, 2, 4}, {1, 2, 3}, {1, 3, 2}, {1, 4, 2}, {3, 2, 5}, {3, 1, 1}, {4, 3, -3}};
    bellmanFord(5, 0, edges);
    return 0;
}
```

---
[➔ Back to Shortest Paths Hub](shortest-paths.md) | [➔ Back to Roadmap](../DSA-Master-Roadmap.md)
