# 61 | Pronic Number

Check if a number is the product of two consecutive integers.

---

## 1. The Objective
A **Pronic Number** (or heteromecic number) is a number which is the product of two consecutive integers, $n(n+1)$.
- **Example:** $12$ ($3 \times 4$)
- **Example:** $20$ ($4 \times 5$)
- **Example:** $42$ ($6 \times 7$)

---

## 2. Visual Logic
### The "Root Search" Strategy
If $x = n(n+1)$, then $n$ must be close to $\sqrt{x}$.
1. Calculate $s = \lfloor \sqrt{x} \rfloor$.
2. Check if $s \times (s+1) == x$.

---

## 3. The "Aha!" Moment
Instead of a slow loop, use the square root to jump directly to the only possible candidate. This makes the check $O(1)$.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <cmath>

/**
 * Strategy: Square Root Candidate check
 * Efficiency: Time O(1)
 */
bool isPronic(int x) {
    if (x < 0) return false;
    if (x == 0) return true; // 0 * 1
    
    int n = sqrt(x);
    return (n * (n + 1) == x);
}

int main() {
    int num = 42;
    if (isPronic(num)) std::cout << num << " is a Pronic number." << std::endl;
    else std::cout << num << " is NOT Pronic." << std::endl;
    return 0;
}
```
