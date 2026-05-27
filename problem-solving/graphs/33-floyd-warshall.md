# 33 | Floyd-Warshall Algorithm

Find shortest paths between **All Pairs** of nodes.

---

## 1. The Objective
Produce a matrix where `mat[i][j]` is the shortest distance from $i$ to $j$.

---

## 2. Visual Logic
### The "Intermediate Node" Strategy
For every pair $(i, j)$, check if passing through an intermediate node $K$ is better.
`dist[i][j] = min(dist[i][j], dist[i][k] + dist[k][j])`

---

## 3. The "Aha!" Moment
This is Dynamic Programming on a 2D grid. It takes $O(V^3)$ time but solves everything in one matrix.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

void floydWarshall(int V, std::vector<std::vector<int>>& dist) {
    for (int k = 0; k < V; k++) {
        for (int i = 0; i < V; i++) {
            for (int j = 0; j < V; j++) {
                if (dist[i][k] != 1e9 && dist[k][j] != 1e9) {
                    dist[i][j] = std::min(dist[i][j], dist[i][k] + dist[k][j]);
                }
            }
        }
    }
}
```
