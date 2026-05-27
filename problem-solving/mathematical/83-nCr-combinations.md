# 83 | Combinations (nCr)

Calculate the number of ways to choose $r$ items from $n$ (order doesn't matter).

---

## 1. The Objective
$C(n, r) = \binom{n}{r} = \frac{n!}{r!(n-r)!}$
**Example:** Choosing 2 people from a group of 3. $C(3, 2) = 3$.

---

## 2. Visual Logic
### The "Relationship" with Permutations
$C(n, r) = \frac{P(n, r)}{r!}$
Every combination is just a permutation where we "cancel out" the different internal orderings of the chosen items.

---

## 3. The "Aha!" Moment
Use the Pascal property: $\binom{n}{r} = \binom{n}{r-1} \times \frac{n-r+1}{r}$. 
This allows you to calculate the combination in $O(r)$ time without any huge intermediate numbers.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy: Incremental Calculation
 */
long long nCr(int n, int r) {
    if (r > n) return 0;
    if (r == 0 || r == n) return 1;
    
    // Optimization: C(n, r) == C(n, n-r)
    if (r > n / 2) r = n - r;
    
    long long res = 1;
    for (int i = 1; i <= r; i++) {
        res = res * (n - i + 1) / i;
    }
    return res;
}

int main() {
    std::cout << "C(5, 2) = " << nCr(5, 2) << std::endl;
    std::cout << "C(50, 5) = " << nCr(50, 5) << std::endl;
    return 0;
}
```
