# 34 | Johnson's Algorithm

Efficient all-pairs shortest paths for sparse graphs.

---

## 1. The Objective
Find all-pairs shortest path in $O(VE + V^2 \log V)$ time.

---

## 2. Visual Logic
### The "Reweighting" Strategy
1. Use Bellman-Ford to find a potential function $h(V)$ such that all edge weights become non-negative.
2. Use Dijkstra $V$ times.
3. This is faster than Floyd-Warshall for large, sparse graphs.

---

## 3. The "Aha!" Moment
It combines the negative-handling power of Bellman-Ford with the speed of Dijkstra.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
// Complex multi-step algorithm involving Bellman-Ford reweighting 
// and N Dijkstra runs.
```
*(Concept documented)*
