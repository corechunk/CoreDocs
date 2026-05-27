# 🌲 DFS (Depth-First Search)

## 1. The Objective
DFS is an algorithm for traversing or searching tree or graph data structures. The algorithm starts at the root node (selecting some arbitrary node as the root node in the case of a graph) and explores as far as possible along each branch before backtracking.

---

## 2. Visual Logic
### Deep Exploration
```text
Path 1: Root -> A -> C (Dead end, backtrack to A)
Path 2: A -> D         (Dead end, backtrack to Root)
Path 3: Root -> B -> E
```

---

## 3. The Logic Bridge
- **The Stack Engine:** DFS uses a **Stack** (either explicitly or via the recursion Call Stack). The last-in-first-out nature forces the algorithm to finish a deep branch before looking at siblings.
- **Reachability:** DFS is the primary tool for finding "Connected Components" and detecting cycles (using the recursion stack to find back-edges).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Recursive)

```cpp
#include <iostream>
#include <vector>

void dfsUtil(int u, const std::vector<std::vector<int>>& adj, std::vector<bool>& visited) {
    visited[u] = true;
    std::cout << u << " ";

    for (int v : adj[u]) {
        if (!visited[v]) {
            dfsUtil(v, adj, visited);
        }
    }
}

void dfs(int start, const std::vector<std::vector<int>>& adj) {
    std::vector<bool> visited(adj.size(), false);
    dfsUtil(start, adj, visited);
}

int main() {
    std::vector<std::vector<int>> adj = {{1, 2}, {0, 3}, {0, 3}, {1, 2}};
    std::cout << "DFS Order: ";
    dfs(0, adj);
    return 0;
}
```

---
[➔ Back to Traversal Hub](graph-traversal.md) | [➔ Back to Roadmap](../DSA-Master-Roadmap.md)
