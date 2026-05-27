# 08 | Edge Count

Calculate the total number of connections in the graph.

---

## 1. The Objective
Return the total number of edges.

---

## 2. Visual Logic
Sum the sizes of all neighbor lists.
`TotalSum = size(adj[0]) + size(adj[1]) + ...`
In an undirected graph, each edge is counted twice. Divide the sum by 2.

---

## 3. The "Aha!" Moment
This is the Handshaking Lemma: $\sum \text{Degree}(V) = 2 \times |E|$.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

int countEdges(const std::vector<std::vector<int>>& adj, bool undirected = true) {
    int total = 0;
    for (int i = 0; i < adj.size(); i++) {
        total += adj[i].size();
    }
    return undirected ? total / 2 : total;
}
```
