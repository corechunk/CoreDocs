# 17 | Find All Paths

Print every possible route from source to destination.

---

## 1. The Objective
Not just the shortest, but **all** of them.

---

## 2. Visual Logic
### The "Backtracking" Explorer
1. Move to neighbor $V$.
2. Add to current `path`.
3. If $V ==$ target: Print path.
4. **UN-MARK** $V$ (visited = false) before returning so other branches can use it.

---

## 3. The "Aha!" Moment
Normal DFS marks a node as visited and **leaves it that way**. Backtracking marks it and then **undoes it** so different paths can cross the same node.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

void findAllPaths(int u, int target, const std::vector<std::vector<int>>& adj, std::vector<bool>& visited, std::vector<int>& path) {
    visited[u] = true;
    path.push_back(u);
    
    if (u == target) {
        for (int x : path) std::cout << x << " ";
        std::cout << std::endl;
    } else {
        for (int v : adj[u]) {
            if (!visited[v]) findAllPaths(v, target, adj, visited, path);
        }
    }
    
    path.pop_back();
    visited[u] = false; // The Backtrack
}
```
