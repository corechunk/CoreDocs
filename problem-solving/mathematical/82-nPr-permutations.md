# 82 | Permutations (nPr)

Calculate the number of ways to arrange $r$ items from a set of $n$.

---

## 1. The Objective
$P(n, r) = \frac{n!}{(n-r)!}$
**Example:** Arranging 3 people in 2 chairs. $P(3, 2) = \frac{3!}{(3-2)!} = \frac{6}{1} = 6$.

---

## 2. Visual Logic
### The "Slot" Strategy
If you have 5 items and 3 slots:
- Slot 1: 5 choices.
- Slot 2: 4 choices.
- Slot 3: 3 choices.
Total: $5 \times 4 \times 3 = 60$.

---

## 3. The "Aha!" Moment
Instead of calculating two massive factorials and dividing (which causes overflow), multiply downwards from $n$ exactly $r$ times.
$P(n, r) = n \times (n-1) \times \dots \times (n-r+1)$.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy: Iterative Multiplication (Avoids Factorial Overflow)
 * Efficiency: Time O(r)
 */
long long nPr(int n, int r) {
    if (r > n) return 0;
    
    long long res = 1;
    for (int i = 0; i < r; i++) {
        res *= (n - i);
    }
    return res;
}

int main() {
    std::cout << "P(10, 3) = " << nPr(10, 3) << std::endl;
    return 0;
}
```
