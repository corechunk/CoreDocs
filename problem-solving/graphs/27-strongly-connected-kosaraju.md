# 27 | Strongly Connected Components (Kosaraju)

Find components where every node can reach every other node (Directed).

---

## 1. The Objective
Divide a digraph into maximal clusters of mutual reachability.

---

## 2. Visual Logic
### The "Reverse and Re-run" Strategy
1. DFS on original graph. Push nodes to stack in finishing order.
2. Reverse the entire graph (flip edges).
3. Pop from stack and start DFS on the reversed graph. Each DFS call reveals one SCC.

---

## 3. The "Aha!" Moment
Reversing the graph preserves the internal connections of an SCC but flips the "order" of connection between different SCCs.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <stack>

// 1. dfs1 (finish order stack)
// 2. reverseAdj
// 3. dfs2 (count components)
```
*(Logic described)*
