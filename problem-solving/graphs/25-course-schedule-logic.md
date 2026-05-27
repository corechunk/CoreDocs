# 25 | Course Schedule Logic

Determine if it's possible to finish all courses given prerequisites.

---

## 1. The Objective
LeetCode classic: Given `[[1,0]]` (to take 1, you must take 0), return `true`.

---

## 2. Visual Logic
This is exactly the **Check if DAG** problem (Problem 23).

---

## 3. The "Aha!" Moment
If the prerequisite graph has a cycle (e.g., A needs B, B needs A), you can never start!

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

/**
 * Strategy: Kahn's or DFS Cycle Detection
 */
bool canFinish(int numCourses, std::vector<std::vector<int>>& prerequisites) {
    // Convert edges to Adjacency List
    // Run isDAG(adj)
    return true;
}
```
