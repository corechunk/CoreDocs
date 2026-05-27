# 07 | Check if Path Exists

Determine if there is any way to travel from point A to point B.

---

## 1. The Objective
Return true if $B$ is reachable from $A$.

---

## 2. Visual Logic
Perform a DFS starting from A. If `visited[B]` becomes true, a path exists.

---

## 3. The "Aha!" Moment
Reachability is the most basic "Connectivity" question. It doesn't care about distance, only existence.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

bool isPath(int u, int target, const std::vector<std::vector<int>>& adj, std::vector<bool>& visited) {
    if (u == target) return true;
    visited[u] = true;
    
    for (int v : adj[u]) {
        if (!visited[v] && isPath(v, target, adj, visited)) return true;
    }
    return false;
}
```
