# 45 | Redundant Connection

Find an edge that can be removed while keeping the graph connected.

---

## 1. The Objective
Identify the edge that creates a cycle in what was supposed to be a tree.

---

## 2. Visual Logic
1. For every edge $(U, V)$:
   - Check `find(U)` and `find(V)`.
   - If they are the same: **This edge is redundant.**
   - Else: `unite(U, V)`.

---

## 3. The "Aha!" Moment
DSU is the perfect "Cycle Detector" for undirected graphs. If you try to join two nodes already in the same set, you have closed a loop.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
// Logic: Iterate through edges and use DSU find/unite.
```
