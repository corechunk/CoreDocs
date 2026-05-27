# 🧗 Topological Sort

## 1. The Objective
Topological Sort is a linear ordering of vertices such that for every directed edge $uv$, vertex $u$ comes before $v$ in the ordering. It is used in **Task Scheduling**, **Build Systems (Makefile)**, and **Compiler Dependency Resolution**.

---

## 2. Visual Logic
### DAG Ordering
Only works on **Directed Acyclic Graphs (DAGs)**.
```text
(A) -> (B) -> (C)
 |             ^
 |---->(D)-----|

Possible Orders: A, B, D, C or A, D, B, C
```

---

## 3. The Logic Bridge
- **In-Degree Logic (Kahn's):** We keep track of how many dependencies (in-degree) each task has. We only process tasks with `in-degree == 0` (no dependencies left).
- **The "Cycle" Test:** If the sorted list doesn't contain all vertices, it means there's a cycle (circular dependency), and a topological sort is impossible.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Kahn's Algorithm)

```cpp
#include <iostream>
#include <vector>
#include <queue>

void topoSort(int n, const std::vector<std::vector<int>>& adj) {
    std::vector<int> in_degree(n, 0);
    for (int u = 0; u < n; u++) {
        for (int v : adj[u]) in_degree[v]++;
    }

    std::queue<int> q;
    for (int i = 0; i < n; i++) {
        if (in_degree[i] == 0) q.push(i);
    }

    std::vector<int> result;
    while (!q.empty()) {
        int u = q.front();
        q.pop();
        result.push_back(u);

        for (int v : adj[u]) {
            if (--in_degree[v] == 0) q.push(v);
        }
    }

    if (result.size() != n) std::cout << "Cycle detected!";
    else {
        for (int x : result) std::cout << x << " ";
    }
}

int main() {
    std::vector<std::vector<int>> adj = {{1, 2}, {3}, {3}, {}};
    topoSort(4, adj);
    return 0;
}
```

---
[➔ Back to Traversal Hub](graph-traversal.md) | [➔ Back to Roadmap](../DSA-Master-Roadmap.md)
