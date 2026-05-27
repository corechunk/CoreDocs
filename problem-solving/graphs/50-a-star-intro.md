# 50 | A* Search Intro

Find shortest path using a heuristic to speed up the search.

---

## 1. The Objective
Solve pathfinding in maps/games more efficiently than Dijkstra.

---

## 2. Visual Logic
### The "Smart" Priority
Instead of picking node with smallest `dist(start, U)`, pick node with smallest:
`f(U) = dist(start, U) + estimate(U, target)`
The `estimate` is usually **Manhattan Distance** (Problem 36 Grid).

---

## 3. The "Aha!" Moment
Dijkstra searches in a circle. A* searches in a "pointed beam" toward the goal.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
// Advanced Dijkstra where priority = cost + heuristic.
```
