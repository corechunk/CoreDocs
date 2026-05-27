# 🛣️ Shortest Path Algorithms

## 1. The Objective
Shortest Path algorithms are designed to find the path between two vertices in a graph such that the sum of the weights of its constituent edges is minimized. This is a critical problem in **Google Maps**, **Network Routing**, and **Logistics**.

---

## 2. Visual Logic
### Weighted Connectivity
```text
(A) --5--> (B) --2--> (C)
 |          ^          ^
 |----10----|          |
 |----------12---------|
```
- Shortest path A -> C is A -> B -> C (Weight 7), not A -> C (Weight 12).

---

## 3. The Logic Bridge
- **Greedy vs. DP:** 
    - **Dijkstra** uses a Greedy approach, always picking the "closest" node next. It only works for non-negative weights.
    - **Bellman-Ford** uses Dynamic Programming, relaxing all edges $V-1$ times. It can handle negative weights.
- **Single Source vs. All-Pairs:** Dijkstra finds paths from one node to all others. **Floyd-Warshall** finds paths between every possible pair of nodes.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Edge Structure)

```cpp
#include <iostream>
#include <vector>

/**
 * Representation for weighted edges.
 */
struct Edge {
    int to;
    int weight;
};

int main() {
    std::vector<std::vector<Edge>> adj(3);
    adj[0].push_back({1, 5}); // A -> B (5)
    adj[1].push_back({2, 2}); // B -> C (2)
    
    std::cout << "Weighted graph initialized." << std::endl;
    return 0;
}
```

---

## 🔗 Sub-Topics (Specific Pathfinding Logic)
- [Dijkstra's Algorithm](dijkstra.md) - Fast, non-negative weights.
- [Bellman-Ford Algorithm](bellman-ford.md) - Handles negative weights.
- [Floyd-Warshall Algorithm](floyd-warshall.md) - All-pairs shortest path.

[➔ Back to Roadmap](../DSA-Master-Roadmap.md)
