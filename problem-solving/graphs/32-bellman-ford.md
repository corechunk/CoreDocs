# 32 | Bellman-Ford Algorithm

Find shortest paths and detect negative cycles.

---

## 1. The Objective
Shortest path in graphs that might have negative edge weights.

---

## 2. Visual Logic
### The "Relaxation" Strategy
1. Relax all edges $(V-1)$ times.
2. `dist[V] = min(dist[V], dist[U] + weight)`.
3. After $V-1$ rounds, try relaxing one more time.
4. If any distance still shrinks, there is a **Negative Cycle**.

---

## 3. The "Aha!" Moment
A path can have at most $V-1$ edges. If it takes more than that to find the minimum, it means you are looping in a negative circle to "generate" infinite negative distance.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

struct Edge { int u, v, w; };

void bellmanFord(int start, int V, const std::vector<Edge>& edges) {
    std::vector<int> dist(V, 1e9);
    dist[start] = 0;
    
    for(int i=0; i<V-1; i++) {
        for(auto e : edges) {
            if(dist[e.u] + e.w < dist[e.v]) dist[e.v] = dist[e.u] + e.w;
        }
    }
}
```
