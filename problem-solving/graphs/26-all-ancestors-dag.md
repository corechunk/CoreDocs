# 26 | All Ancestors in a DAG

Find all nodes that can reach node $U$.

---

## 1. The Objective
Given a DAG, for every node, list its ancestors.

---

## 2. Visual Logic
### The "Reverse Search" Strategy
For every node, start a DFS on the **Reversed Graph** (all edge directions flipped). Every node reachable from $U$ in the reversed graph is an ancestor of $U$ in the original.

---

## 3. The "Aha!" Moment
Ancestry is just reachability in reverse.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <set>

void getAncestors(int u, const std::vector<std::vector<int>>& revAdj, std::set<int>& s) {
    for (int v : revAdj[u]) {
        if (s.find(v) == s.end()) {
            s.insert(v);
            getAncestors(v, revAdj, s);
        }
    }
}
```
