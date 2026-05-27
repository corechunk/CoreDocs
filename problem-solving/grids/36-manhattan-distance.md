# 36 | Manhattan Distance

Calculate the "Taxicab" distance between two points on a grid.

---

## 1. The Objective
Given $(x_1, y_1)$ and $(x_2, y_2)$, find the distance if you can only move horizontally and vertically.

---

## 2. Visual Logic
```text
Dist = |x1 - x2| + |y1 - y2|
```
It’s called Manhattan distance because it represents how many blocks a taxi has to drive in a grid-like city.

---

## 3. The "Aha!" Moment
This is used in pathfinding heuristics (like A*) because it correctly models grid-based movement costs.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <cmath>

int manhattanDist(int r1, int c1, int r2, int c2) {
    return std::abs(r1 - r2) + std::abs(c1 - c2);
}

int main() {
    std::cout << "Distance (0,0) to (3,3): " << manhattanDist(0, 0, 3, 3) << std::endl;
    return 0;
}
```
