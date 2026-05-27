# 13 | Cycle Detection (Directed)

Check if a directed graph (digraph) contains a loop.

---

## 1. The Objective
Return true if a path exists from $V$ back to $V$.

---

## 2. Visual Logic
### The "Recursion Stack" Filter
A visited array isn't enough (a node can be visited via two different paths without a cycle). You must track if a node is currently "active" in the recursion.
1. `visited[]`: Permanent mark.
2. `recursionStack[]`: "Processing" mark.
If you hit an `active` node, you found a cycle.

---

## 3. The "Aha!" Moment
Think of it like a trace. If you run into yourself while drawing the path, you are in a loop.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

bool hasCycleDirected(int u, const std::vector<std::vector<int>>& adj, std::vector<bool>& visited, std::vector<bool>& stack) {
    visited[u] = stack[u] = true;
    
    for (int v : adj[u]) {
        if (!visited[v] && hasCycleDirected(v, adj, visited, stack)) return true;
        if (stack[v]) return true;
    }
    
    stack[u] = false; // Clean up as we backtrack
    return false;
}
```
