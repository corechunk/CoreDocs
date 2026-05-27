# 07 | Largest of Three Numbers

Find the maximum value among three given numbers.

---

## 1. The Objective
Given `a`, `b`, and `c`, determine which one is the largest.

---

## 2. Visual Logic
### The Tournament Strategy
1. Compare `a` and `b`. The winner goes to the final.
2. Compare the winner with `c`. The final winner is the largest.

```text
       [a] vs [b]
          |
       (Winner) vs [c]
              |
          [Largest]
```

---

## 3. The "Aha!" Moment
- **Nested Ifs:** Explicitly check every condition.
- **Ternary Operators:** Compact, one-line logic.
- **`std::max`:** Using built-in efficiency.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <algorithm> // for std::max

/**
 * Strategy A: Nested If-Else (The Explicit Way)
 */
int findMaxExplicit(int a, int b, int c) {
    if (a >= b && a >= c) return a;
    if (b >= a && b >= c) return b;
    return c;
}

/**
 * Strategy B: Ternary Operator (The Concise Way)
 */
int findMaxTernary(int a, int b, int c) {
    return (a > b) ? ((a > c) ? a : c) : ((b > c) ? b : c);
}

/**
 * Strategy C: Built-in Library (The Pro Way)
 */
int findMaxLibrary(int a, int b, int c) {
    return std::max({a, b, c});
}

int main() {
    int x = 10, y = 25, z = 15;
    
    std::cout << "Largest (Explicit): " << findMaxExplicit(x, y, z) << std::endl;
    std::cout << "Largest (Ternary): " << findMaxTernary(x, y, z) << std::endl;
    std::cout << "Largest (Library): " << findMaxLibrary(x, y, z) << std::endl;
    
    return 0;
}
```
