# 12 | Cycle Detection (Undirected)

Check if an undirected graph contains a loop.

---

## 1. The Objective
Return true if any node can reach itself without immediate backtracking.

---

## 2. Visual Logic
### The "Back-Edge" Rule
If you are at node $U$, and you visit neighbor $V$:
- If $V$ is already visited AND $V$ is NOT the parent of $U$: **A Cycle exists.**

---

## 3. The "Aha!" Moment
In undirected graphs, we must ignore the parent we just came from. Any other "visited" neighbor represents a second path to the same place.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

bool hasCycleUndirected(int u, int parent, const std::vector<std::vector<int>>& adj, std::vector<bool>& visited) {
    visited[u] = true;
    for (int v : adj[u]) {
        if (!visited[v]) {
            if (hasCycleUndirected(v, u, adj, visited)) return true;
        } else if (v != parent) {
            return true; // Found a cycle
        }
    }
    return false;
}
```
