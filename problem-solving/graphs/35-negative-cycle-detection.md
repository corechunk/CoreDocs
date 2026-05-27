# 35 | Negative Cycle Detection

Check if a graph has a loop with a negative total weight.

---

## 1. The Objective
Prevent infinite loops in shortest path calculations.

---

## 2. Visual Logic
Perform a $V^{th}$ relaxation in Bellman-Ford. If anything changes, a cycle exists.

---

## 3. The "Aha!" Moment
Negative cycles are important in finance (arbitrage) where you want to find loops that increase value (or decrease cost) indefinitely.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
// Logic integrated in Bellman-Ford (Problem 32)
```
