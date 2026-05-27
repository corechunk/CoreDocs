# 02 | Adjacency List

Represent a graph using an array of lists.

---

## 1. The Objective
Store only the connections that actually exist to save space.

---

## 2. Visual Logic
### The "Neighbor Map"
```text
Node 0 -> [1]
Node 1 -> [0, 2]
Node 2 -> [1]
```

---

## 3. The "Aha!" Moment
Instead of a $V \times V$ grid, each node $i$ has a dynamic list of its neighbors. This uses $O(V + E)$ space, making it the industry standard for representing large networks.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <list>

/**
 * Strategy: Vector of Lists/Vectors
 */
class GraphList {
    int V;
    std::vector<std::vector<int>> adj;

public:
    GraphList(int nodes) : V(nodes) {
        adj.resize(V);
    }

    void addEdge(int u, int v) {
        adj[u].push_back(v);
        adj[v].push_back(u); // Undirected
    }

    void print() {
        for (int i = 0; i < V; i++) {
            std::cout << i << ": ";
            for (int neighbor : adj[i]) std::cout << neighbor << " ";
            std::cout << std::endl;
        }
    }
};

int main() {
    GraphList g(4);
    g.addEdge(0, 1);
    g.addEdge(0, 2);
    g.addEdge(1, 3);
    g.print();
    return 0;
}
```
