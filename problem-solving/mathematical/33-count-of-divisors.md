# 33 | Count of Divisors

Determine how many divisors a number has.

---

## 1. The Objective
Given `n = 12`, divisors are `1, 2, 3, 4, 6, 12`.
Count = `6`.

---

## 2. Visual Logic
### The Prime Power Strategy (Advanced)
If $n = p_1^a \times p_2^b \times \dots$, then the count of divisors is $(a+1)(b+1)\dots$
- $12 = 2^2 \times 3^1$
- Count = $(2+1) \times (1+1) = 3 \times 2 = 6$.

---

## 3. The "Aha!" Moment
For small numbers, use the $O(\sqrt{n})$ counter. For massive numbers, perform prime factorization and multiply the (exponents + 1).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy: O(sqrt n) Counter
 */
int countDivisors(int n) {
    int count = 0;
    for (int i = 1; i * i <= n; i++) {
        if (n % i == 0) {
            if (i * i == n) count += 1;
            else count += 2;
        }
    }
    return count;
}

int main() {
    int num = 36;
    std::cout << "Number of divisors in " << num << ": " << countDivisors(num) << std::endl;
    return 0;
}
```
