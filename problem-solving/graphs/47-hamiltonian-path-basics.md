# 47 | Hamiltonian Path Basics

Visit every node exactly once.

---

## 1. The Objective
Find a path that touches every vertex without repeats.

---

## 2. Visual Logic
This is an NP-Complete problem. For small graphs, use **Backtracking** to try every combination.

---

## 3. The "Aha!" Moment
Unlike Eulerian paths (easy to check), Hamiltonian paths are mathematically "Hard" to find and verify.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
// Logic: Backtracking DFS with path.size() == V check.
```
