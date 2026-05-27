# 78 | Trailing Zeros in Factorial

Count how many zeros are at the end of $n!$.

---

## 1. The Objective
Given `n = 10`, $10! = 3,628,800$. Return `2`.
**Constraint:** Do not calculate the factorial (it overflows fast).

---

## 2. Visual Logic
### The "Factor 5" Strategy
A trailing zero is created by $2 \times 5$. 
In any factorial, there are plenty of 2s (every even number). The limiting factor is the number of 5s.
- $5$ contributes one 5.
- $10$ contributes one 5.
- $25$ contributes **two** 5s ($5 \times 5$).

---

## 3. The "Aha!" Moment
Count how many multiples of 5, 25, 125, etc., are in $n$.
$\text{Zeros} = \lfloor \frac{n}{5} \rfloor + \lfloor \frac{n}{25} \rfloor + \lfloor \frac{n}{125} \rfloor \dots$

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy: Legendre's Formula for Prime 5
 * Efficiency: Time O(log5 n)
 */
int countTrailingZeros(int n) {
    int count = 0;
    // Divide n by powers of 5 and sum the quotients
    for (int i = 5; n / i >= 1; i *= 5) {
        count += n / i;
    }
    return count;
}

int main() {
    int n = 100;
    std::cout << "Trailing zeros in " << n << "!: " << countTrailingZeros(n) << std::endl;
    return 0;
}
```
