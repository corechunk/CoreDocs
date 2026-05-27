# ⚡ Prim's Algorithm

## 1. The Objective
Prim's algorithm is a greedy algorithm that finds a Minimum Spanning Tree for a weighted undirected graph. It works by growing the spanning tree from a single starting vertex, adding the cheapest vertex that is not yet in the tree.

---

## 2. Visual Logic
### The Growing Tree
1. Start with any vertex.
2. Maintain a set of vertices already in the MST.
3. At each step, pick the **cheapest edge** that connects a vertex in the set to a vertex outside the set.

---

## 3. The Logic Bridge
- **The "Local" Choice:** Unlike Kruskal's (which considers all edges at once), Prim's focus is on "where we can go next from our current tree". 
- **The Priority Queue Engine:** We use a **Min-Priority Queue** to store edges connected to our growing MST. This allows us to find the next cheapest vertex in $O(\log V)$ time.
- **Dense Graphs:** Prim's (with Fibonacci Heap) can be faster than Kruskal's for very dense graphs where $E \approx V^2$.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Priority Queue)

```cpp
#include <iostream>
#include <vector>
#include <queue>

typedef std::pair<int, int> pii;

int prim(int n, const std::vector<std::vector<pii>>& adj) {
    std::priority_queue<pii, std::vector<pii>, std::greater<pii>> pq;
    std::vector<bool> inMST(n, false);
    int mst_weight = 0;

    pq.push({0, 0}); // {weight, vertex}

    while (!pq.empty()) {
        int w = pq.top().first;
        int u = pq.top().second;
        pq.pop();

        if (inMST[u]) continue;

        inMST[u] = true;
        mst_weight += w;

        for (auto& edge : adj[u]) {
            int v = edge.first;
            int weight = edge.second;
            if (!inMST[v]) pq.push({weight, v});
        }
    }
    return mst_weight;
}

int main() {
    std::vector<std::vector<pii>> adj = {{{1, 10}, {2, 6}, {3, 5}}, {{0, 10}, {3, 15}}, {{0, 6}, {3, 4}}, {{0, 5}, {1, 15}, {2, 4}}};
    std::cout << "MST Weight (Prim): " << prim(4, adj) << std::endl;
    return 0;
}
```

---
[➔ Back to MST Hub](minimum-spanning-tree.md) | [➔ Back to Roadmap](../DSA-Master-Roadmap.md)
