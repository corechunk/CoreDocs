# 37 | Cheapest Flights with K Stops

Shortest path with a constraint on the number of edges.

---

## 1. The Objective
Find min cost from A to B using at most $K$ intermediate nodes.

---

## 2. Visual Logic
### The "Level-Limited" BFS
Use BFS but track levels. Stop exploring after $K+1$ levels.

---

## 3. The "Aha!" Moment
A standard shortest path doesn't work because the cheapest path might have 10 stops, but you are only allowed 2. You must find the best path within the limit.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <queue>

int findCheapest(int n, std::vector<std::vector<int>>& flights, int src, int dst, int K) {
    // BFS with limited depth and cost tracking
    return 0;
}
```
