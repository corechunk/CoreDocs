# 37 | Euclidean Distance

Calculate the straight-line distance between two points.

---

## 1. The Objective
Find the "as the crow flies" distance using the Pythagorean theorem.

---

## 2. Visual Logic
```text
Dist = sqrt( (x1-x2)^2 + (y1-y2)^2 )
```

---

## 3. The "Aha!" Moment
This results in a floating-point number. Use `double` for calculation.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <cmath>

double euclideanDist(double r1, double c1, double r2, double c2) {
    return sqrt(pow(r1 - r2, 2) + pow(c1 - c2, 2));
}

int main() {
    std::cout << "Dist: " << euclideanDist(0, 0, 3, 4) << std::endl; // Should be 5.0
    return 0;
}
```
