# 09 | Node Degree

Calculate how many edges are connected to a specific node.

---

## 1. The Objective
Find the degree of vertex $V$.
- **Undirected:** Simple count of neighbors.
- **Directed:** In-degree (entering) and Out-degree (leaving).

---

## 2. Visual Logic
Degree = `adj[V].size()`.

---

## 3. The "Aha!" Moment
A "Self-loop" (edge from V to V) counts as 2 degrees in many mathematical definitions, but in simple programming, it's just one entry in the list.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

int getDegree(int u, const std::vector<std::vector<int>>& adj) {
    return adj[u].size();
}
```
