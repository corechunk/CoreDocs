# 29 | Articulation Points

Identify nodes whose removal would disconnect the graph.

---

## 1. The Objective
Find "Single Points of Failure" in a network.

---

## 2. Visual Logic
### The "Cut-Vertex" Condition
Node $U$ is an articulation point if:
1. It is Root and has $> 1$ child.
2. It is not Root and has a child $V$ such that no node in $V$'s subtree has a "back-edge" to $U$ or any of $U$'s ancestors.

---

## 3. The "Aha!" Moment
If a child cannot "climb back up" without passing through the parent, then the parent is a bottleneck.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

void findAP(int u, int& timer, ...) {
    // DFS tracking disc[] and low[]
    // if (low[v] >= disc[u]) AP[u] = true;
}
```
