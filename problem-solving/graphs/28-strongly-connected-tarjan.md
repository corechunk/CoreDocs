# 28 | SCCs (Tarjan's Algorithm)

Find strongly connected components in a single pass.

---

## 1. The Objective
Identify mutual reachability clusters more efficiently than Kosaraju.

---

## 2. Visual Logic
### The "Low-Link" Strategy
Track `discoveryTime[U]` and `lowLink[U]` (the earliest node reachable from U). If `discoveryTime == lowLink`, $U$ is the "head" of an SCC.

---

## 3. The "Aha!" Moment
Tarjan's uses a single DFS and a stack to identify "cycles of reachability" as it finds them.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <stack>
#include <algorithm>

// Complex DFS with disc[] and low[] arrays
```
