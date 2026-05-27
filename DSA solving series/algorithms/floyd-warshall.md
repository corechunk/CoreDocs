# 🕸️ Floyd-Warshall Algorithm

## 1. The Objective
The Floyd-Warshall algorithm is an **All-Pairs Shortest Path** algorithm. It finds the shortest distances between every single pair of vertices in a weighted graph (directed or undirected), even with negative weights (but no negative cycles).

---

## 2. Visual Logic
### The Intermediate Node Matrix
```text
dist[i][j] = shortest path from i to j.
For each intermediate node 'k':
  For each source 'i':
    For each destination 'j':
      dist[i][j] = min(dist[i][j], dist[i][k] + dist[k][j])
```

---

## 3. The Logic Bridge
- **Dynamic Programming Power:** We build the solution by considering increasingly larger sets of intermediate nodes. `dist[i][j]` initially uses no intermediate nodes (direct edges), then we allow node 1, then node 1 and 2, and so on.
- **The Triple Loop:** Because we check every triplet $(i, j, k)$, the complexity is **$O(V^3)$**. This makes it perfect for dense graphs with up to ~500 nodes.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

const int INF = 1e9;

void floydWarshall(int n, std::vector<std::vector<int>>& dist) {
    for (int k = 0; k < n; k++) {
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                if (dist[i][k] != INF && dist[k][j] != INF)
                    dist[i][j] = std::min(dist[i][j], dist[i][k] + dist[k][j]);
            }
        }
    }
}

int main() {
    int n = 4;
    std::vector<std::vector<int>> dist = {
        {0, 5, INF, 10},
        {INF, 0, 3, INF},
        {INF, INF, 0, 1},
        {INF, INF, INF, 0}
    };

    floydWarshall(n, dist);

    std::cout << "Shortest distance matrix:\n";
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            if (dist[i][j] == INF) std::cout << "INF ";
            else std::cout << dist[i][j] << " ";
        }
        std::cout << "\n";
    }
    return 0;
}
```

---
[➔ Back to Shortest Paths Hub](shortest-paths.md) | [➔ Back to Roadmap](../DSA-Master-Roadmap.md)
