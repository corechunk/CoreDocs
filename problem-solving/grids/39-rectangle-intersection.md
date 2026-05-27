# 39 | Rectangle Intersection

Check if two rectangles overlap.

---

## 1. The Objective
Return true if any part of Rectangle A is inside Rectangle B.

---

## 2. Visual Logic
### The "Separating Axis" Strategy
It is easier to check if they **don't** overlap and then negate the result.
Two rectangles **don't** overlap if:
- A is entirely to the Left of B.
- A is entirely to the Right of B.
- A is entirely Above B.
- A is entirely Below B.

---

## 3. The "Aha!" Moment
```text
overlap = !(left1 > right2 || right1 < left2 || top1 > bottom2 || bottom1 < top2)
```

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

struct Rect { int x1, y1, x2, y2; };

bool intersects(Rect a, Rect b) {
    if (a.x1 > b.x2 || b.x1 > a.x2) return false;
    if (a.y1 > b.y2 || b.y1 > a.y2) return false;
    return true;
}

int main() {
    Rect r1 = {0, 0, 10, 10};
    Rect r2 = {5, 5, 15, 15};
    std::cout << "Overlap? " << intersects(r1, r2) << std::endl;
    return 0;
}
```
