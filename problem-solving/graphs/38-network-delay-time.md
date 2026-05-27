# 38 | Network Delay Time

Calculate how long it takes for a signal from $S$ to reach all nodes.

---

## 1. The Objective
The answer is the **maximum** of the shortest paths from $S$ to every other node.

---

## 2. Visual Logic
1. Run Dijkstra from $S$.
2. The `max(dist[0...V-1])` is your answer.

---

## 3. The "Aha!" Moment
The signal only travels as fast as the "slowest" (furthest) shortest path.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
// Logic: Run Dijkstra and find max value in dist array.
```
