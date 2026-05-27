# 39 | Min Cost to Connect All Points

Find the shortest network that connects every node (no cycles).

---

## 1. The Objective
Connect $N$ points in a 2D plane with minimum total wire length.

---

## 2. Visual Logic
This is a **Minimum Spanning Tree (MST)** problem.

---

## 3. The "Aha!" Moment
Use Prim's or Kruskal's algorithm on a fully connected graph where edge weight is the Manhattan/Euclidean distance.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
// Logic: Calculate all-pairs distances, then run MST algorithm.
```
