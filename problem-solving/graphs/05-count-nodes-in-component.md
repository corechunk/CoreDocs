# 05 | Count Nodes in a Component

Find how many nodes are connected together in a specific subgraph.

---

## 1. The Objective
Given a node, count how many other nodes can be reached from it.

---

## 2. Visual Logic
Start a traversal (BFS or DFS). Instead of printing, increment a counter for every new node you visit.

---

## 3. The "Aha!" Moment
The total count of visited nodes in one DFS call is the size of that connected component.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

void countUtil(int u, const std::vector<std::vector<int>>& adj, std::vector<bool>& visited, int& count) {
    visited[u] = true;
    count++;
    for (int v : adj[u]) {
        if (!visited[v]) countUtil(v, adj, visited, count);
    }
}

int componentSize(int start, const std::vector<std::vector<int>>& adj) {
    std::vector<bool> visited(adj.size(), false);
    int count = 0;
    countUtil(start, adj, visited, count);
    return count;
}
```
