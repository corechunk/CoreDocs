# 44 | DSU Path Compression & Rank

Optimize Union-Find to near-instant speed.

---

## 1. The Objective
Prevent the family tree from becoming a long chain (slow search).

---

## 2. Visual Logic
1. **Path Compression:** When doing `find(X)`, make every node in the path point **directly** to the leader.
2. **Union by Rank:** Always attach the shorter tree under the taller tree.

---

## 3. The "Aha!" Moment
Path compression flattens the tree structure every time you look something up, making the next lookup even faster.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
int find(int i) {
    if (parent[i] == i) return i;
    return parent[i] = find(parent[i]); // Path compression
}
```
*(Optimization on Problem 43)*
