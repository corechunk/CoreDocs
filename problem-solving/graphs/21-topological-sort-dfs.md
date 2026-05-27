# 21 | Topological Sort (DFS)

Order the nodes of a DAG (Directed Acyclic Graph) such that for every edge $(U, V)$, $U$ comes before $V$.

---

## 1. The Objective
Solve dependencies (like university course prerequisites or build tasks).

---

## 2. Visual Logic
### The "Finish Stack"
1. Perform DFS.
2. When a node is **completely finished** (all neighbors visited), push it onto a stack.
3. The stack, when popped, gives the topological order.

---

## 3. The "Aha!" Moment
Topological sorting is only possible if there are **No Cycles**. The nodes that finish last in a DFS are the "deepest" dependencies and should appear at the end.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <stack>

void topoDFS(int u, const std::vector<std::vector<int>>& adj, std::vector<bool>& visited, std::stack<int>& s) {
    visited[u] = true;
    for (int v : adj[u]) {
        if (!visited[v]) topoDFS(v, adj, visited, s);
    }
    s.push(u); // Node finished
}

void topologicalSort(const std::vector<std::vector<int>>& adj) {
    std::stack<int> s;
    std::vector<bool> visited(adj.size(), false);
    for (int i = 0; i < adj.size(); i++) {
        if (!visited[i]) topoDFS(i, adj, visited, s);
    }
    while (!s.empty()) { std::cout << s.top() << " "; s.pop(); }
}
```
