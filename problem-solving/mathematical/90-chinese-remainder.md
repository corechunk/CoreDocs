# 90 | Chinese Remainder Theorem (Basics)

Solve systems of simultaneous congruences.

---

## 1. The Objective
Find $x$ such that:
- $x \pmod 3 = 2$
- $x \pmod 5 = 3$
- $x \pmod 7 = 2$

---

## 2. Visual Logic
### The "Common Ground" Strategy
1. Start with the largest modulo (7). Candidate $x = 2$ (since $2 \pmod 7 = 2$).
2. Add 7 until $x \pmod 5 = 3$.
   - $2, 9, 16, 23 \dots$ ($23 \pmod 5 = 3$). New $x = 23$.
3. Now add $(7 \times 5 = 35)$ until $x \pmod 3 = 2$.
   - $23 \pmod 3 = 2$. **Target Reached!** Result: $23$.

---

## 3. The "Aha!" Moment
If all moduli are co-prime, a unique solution exists within the range $[0, \text{Product of moduli}]$. You can solve it by iteratively jumping by the "Product of moduli seen so far."

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

/**
 * Strategy: Iterative Search with Jumping
 */
long long findCRT(const std::vector<int>& rem, const std::vector<int>& num) {
    long long x = rem[0];
    long long product = num[0];
    
    for (int i = 1; i < num.size(); i++) {
        while (x % num[i] != rem[i]) {
            x += product;
        }
        product *= num[i];
    }
    return x;
}

int main() {
    std::vector<int> rem = {2, 3, 2};
    std::vector<int> num = {3, 5, 7};
    std::cout << "Solution x: " << findCRT(rem, num) << std::endl;
    return 0;
}
```
