# 🌊 BFS (Breadth-First Search)

## 1. The Objective
BFS is an algorithm for traversing or searching tree or graph data structures. It starts at an arbitrary node and explores all neighbor nodes at the present depth prior to moving on to the nodes at the next depth level.

---

## 2. Visual Logic
### Level-by-Level Discovery
```text
Level 0:    [ Root ]
              /   \
Level 1:    [A]   [B]
            / \     \
Level 2:  [C] [D]   [E]

Visit Order: Root -> A -> B -> C -> D -> E
```

---

## 3. The Logic Bridge
- **The Queue Engine:** BFS is inherently iterative. We use a **Queue** to store nodes that are discovered but not yet explored. The first-in-first-out nature guarantees that we process all nodes at distance $K$ before any node at distance $K+1$.
- **Shortest Path:** In an unweighted graph, BFS is **guaranteed** to find the shortest path between two nodes because it explores the graph in increasing order of distance.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <queue>

void bfs(int start, const std::vector<std::vector<int>>& adj) {
    std::vector<bool> visited(adj.size(), false);
    std::queue<int> q;

    visited[start] = true;
    q.push(start);

    while (!q.empty()) {
        int u = q.front();
        q.pop();
        std::cout << u << " ";

        for (int v : adj[u]) {
            if (!visited[v]) {
                visited[v] = true;
                q.push(v);
            }
        }
    }
}

int main() {
    std::vector<std::vector<int>> adj = {{1, 2}, {0, 3}, {0, 3}, {1, 2}};
    std::cout << "BFS Order: ";
    bfs(0, adj);
    return 0;
}
```

---
[➔ Back to Traversal Hub](graph-traversal.md) | [➔ Back to Roadmap](../DSA-Master-Roadmap.md)
