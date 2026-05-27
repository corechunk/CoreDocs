# 38 | Point in Rectangle

Check if a coordinate $(x, y)$ is inside a defined rectangular area.

---

## 1. The Objective
Given `(top, left)` and `(bottom, right)`, is the point `(px, py)` inside?

---

## 2. Visual Logic
### The "Bounds" Check
1. `px >= left` AND `px <= right`
2. `py >= top` AND `py <= bottom`

---

## 3. The "Aha!" Moment
This is the core logic for **Collision Detection** in 2D games and user interface buttons.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

bool isInside(int px, int py, int left, int top, int right, int bottom) {
    return (px >= left && px <= right && py >= top && py <= bottom);
}

int main() {
    if (isInside(5, 5, 0, 0, 10, 10)) {
        std::cout << "Inside!" << std::endl;
    }
    return 0;
}
```
