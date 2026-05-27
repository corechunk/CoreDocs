# 49 | Min-Cut Max-Flow

Determine the maximum capacity of a network.

---

## 1. The Objective
How much water/data can flow from Source to Sink?

---

## 2. Visual Logic
### The "Residual Graph"
1. Find a path with available capacity.
2. "Push" flow through it.
3. Update remaining capacity.
4. Repeat until no more paths exist.

---

## 3. The "Aha!" Moment
The **Max Flow** through a network is always equal to the **Minimum Cut** (the set of edges that, if removed, would stop all flow).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
// Algorithm: Edmonds-Karp (BFS version of Ford-Fulkerson).
```
