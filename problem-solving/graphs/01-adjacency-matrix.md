# 01 | Adjacency Matrix

Represent a graph using a 2D array.

---

## 1. The Objective
Create a fixed-size representation of a graph where `matrix[i][j] = 1` means an edge exists between node `i` and node `j`.

---

## 2. Visual Logic
### The "Connection Table"
```text
Nodes: 0, 1, 2
Edges: (0-1), (1-2)

Matrix:
    0 1 2
0 [ 0 1 0 ]
1 [ 1 0 1 ]
2 [ 0 1 0 ]
```

---

## 3. The "Aha!" Moment
An Adjacency Matrix allows for $O(1)$ edge existence checks. If you want to know if 0 is connected to 1, you just check `mat[0][1]`. However, it uses $O(V^2)$ space, which is wasteful for "sparse" graphs with few edges.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

/**
 * Strategy: 2D Vector Representation
 */
class GraphMatrix {
    int V;
    std::vector<std::vector<int>> adj;

public:
    GraphMatrix(int nodes) : V(nodes) {
        adj.resize(V, std::vector<int>(V, 0));
    }

    void addEdge(int u, int v) {
        adj[u][v] = 1;
        adj[v][u] = 1; // For undirected graph
    }

    void print() {
        for (int i = 0; i < V; i++) {
            for (int j = 0; j < V; j++) {
                std::cout << adj[i][j] << " ";
            }
            std::cout << std::endl;
        }
    }
};

int main() {
    GraphMatrix g(3);
    g.addEdge(0, 1);
    g.addEdge(1, 2);
    g.print();
    return 0;
}
```
