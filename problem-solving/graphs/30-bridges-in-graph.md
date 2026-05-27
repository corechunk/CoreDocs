# 30 | Bridges in Graph

Identify edges whose removal would disconnect the graph.

---

## 1. The Objective
Find "Critical Connections."

---

## 2. Visual Logic
### The "Cut-Edge" Condition
Edge $(U, V)$ is a bridge if `low[V] > disc[U]`. This means $V$ has absolutely no way to reach $U$ or above without using the $(U, V)$ edge.

---

## 3. The "Aha!" Moment
Bridges represent unique paths. If you delete them, you break the bridge between two islands.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

void findBridges(int u, int p, ...) {
    // low[v] > disc[u] -> Bridge found!
}
```
