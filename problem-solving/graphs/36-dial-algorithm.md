# 36 | Dial's Algorithm

Optimization of Dijkstra for small integer weights.

---

## 1. The Objective
If edge weights are small (max weight $W$), find shortest path in $O(E + VW)$.

---

## 2. Visual Logic
### The "Bucket" Dijkstra
Instead of a Priority Queue, use an array of buckets `dist % (W + 1)`.

---

## 3. The "Aha!" Moment
This is a "Bucket Sort" version of Dijkstra's.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
// Specialist variant of Dijkstra using circular buckets.
```
