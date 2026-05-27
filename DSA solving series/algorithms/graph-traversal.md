# 🕸️ Graph Traversals (Exploring Networks)

## 1. The Objective
Graph Traversal is the process of visiting all the nodes in a graph exactly once in a specific order. It is the foundation for solving connectivity problems, pathfinding, and cycle detection.

---

## 2. Visual Logic
### The Search Pattern
- **Breadth-First (BFS):** Explore all neighbors at distance 1, then distance 2... (Like a ripple in a pond).
- **Depth-First (DFS):** Go as deep as possible along a path before backtracking (Like exploring a maze).

---

## 3. The Logic Bridge
- **The "State" Tracker:** Unlike trees, graphs can have cycles. To avoid infinite loops, we **must** maintain a `visited[]` array to track which nodes have already been processed.
- **Queue vs. Stack:** 
    - A **Queue** leads to a level-by-level discovery (BFS).
    - A **Stack** (or Recursion) leads to a depth-first discovery (DFS).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Abstract Adjacency List)

```cpp
#include <iostream>
#include <vector>

/**
 * Common graph representation for traversal.
 */
struct Graph {
    int V;
    std::vector<std::vector<int>> adj;

    Graph(int v) : V(v) { adj.resize(v); }
    void addEdge(int u, int v) {
        adj[u].push_back(v);
        adj[v].push_back(u); // Undirected
    }
};

int main() {
    Graph g(4);
    g.addEdge(0, 1);
    g.addEdge(1, 2);
    g.addEdge(2, 3);
    
    std::cout << "Graph initialized with " << g.V << " vertices." << std::endl;
    return 0;
}
```

---

## 🔗 Sub-Topics (Specific Traversal Logic)
- [BFS (Breadth-First Search)](bfs.md) - Shortest path in unweighted graphs.
- [DFS (Depth-First Search)](dfs.md) - Connectivity & Cycle detection.
- [Topological Sort](topological-sort.md) - Task scheduling logic.

[➔ Back to Roadmap](../DSA-Master-Roadmap.md)
