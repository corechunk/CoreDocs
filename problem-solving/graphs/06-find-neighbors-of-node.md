# 06 | Find Neighbors of a Node

Retrieve all nodes directly connected to target `U`.

---

## 1. The Objective
Given target node $U$, list its adjacent vertices.

---

## 2. Visual Logic
In an Adjacency List, this is simply the list stored at index `adj[U]`.

---

## 3. The "Aha!" Moment
Finding neighbors is $O(\text{Degree of } U)$. In an Adjacency Matrix, it is $O(V)$ because you must scan the entire row.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

void printNeighbors(int u, const std::vector<std::vector<int>>& adj) {
    std::cout << "Neighbors of " << u << ": ";
    for (int v : adj[u]) {
        std::cout << v << " ";
    }
    std::cout << std::endl;
}
```
