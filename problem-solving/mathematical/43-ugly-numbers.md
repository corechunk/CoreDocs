# 43 | Ugly Numbers

Check if a number has only 2, 3, or 5 as its prime factors.

---

## 1. The Objective
**Ugly Numbers** are positive integers whose prime factors only include 2, 3, and 5.
- **Example:** $1, 2, 3, 4, 5, 6, 8, 9, 10, 12, 15, \dots$
- **Example:** $14$ is NOT ugly (factor 7).
- **Example:** $21$ is NOT ugly (factor 7).

---

## 2. Visual Logic
### The "Reduction" Strategy (n=300)
1. Keep dividing by 2: $300 \to 150 \to 75$.
2. Keep dividing by 3: $75 \to 25$.
3. Keep dividing by 5: $25 \to 5 \to 1$.
If you reach **1**, the number is Ugly.

---

## 3. The "Aha!" Moment
If a number is only made of factors 2, 3, and 5, then dividing by them repeatedly **must** result in 1. If it stops at something else (like 7 or 11), it's not ugly.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy: Repeated Division
 */
bool isUgly(int n) {
    if (n <= 0) return false;
    
    int factors[] = {2, 3, 5};
    for (int f : factors) {
        while (n % f == 0) {
            n /= f;
        }
    }
    
    return n == 1;
}

int main() {
    int num = 120;
    if (isUgly(num)) std::cout << num << " is an Ugly number." << std::endl;
    else std::cout << num << " is NOT Ugly." << std::endl;
    return 0;
}
```
