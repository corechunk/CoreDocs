# 23 | Check if DAG

Determine if a directed graph has zero cycles.

---

## 1. The Objective
Return true if the graph is a Directed Acyclic Graph.

---

## 2. Visual Logic
Reuse Kahn's Algorithm (Problem 22). If you can successfully perform a full topological sort, it is a DAG.

---

## 3. The "Aha!" Moment
A DAG is a "Hierarchy." If there's a loop, the concept of "Parent/Child" or "Pre-requisite" breaks down.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <queue>

bool isDAG(const std::vector<std::vector<int>>& adj) {
    int V = adj.size();
    std::vector<int> inDegree(V, 0);
    for (int i = 0; i < V; i++) for (int v : adj[i]) inDegree[v]++;
    
    std::queue<int> q;
    for (int i = 0; i < V; i++) if (inDegree[i] == 0) q.push(i);
    
    int visited = 0;
    while (!q.empty()) {
        int u = q.front(); q.pop();
        visited++;
        for (int v : adj[u]) if (--inDegree[v] == 0) q.push(v);
    }
    return visited == V;
}
```
