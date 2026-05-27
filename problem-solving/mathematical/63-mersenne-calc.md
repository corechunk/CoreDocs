# 63 | Mersenne Number Calculation

Calculate numbers of the form $2^n - 1$.

---

## 1. The Objective
A **Mersenne Number** is defined as $M_n = 2^n - 1$.
Generate the sequence of Mersenne numbers.

---

## 2. Visual Logic
### The "One-Less-Than-Power" Sequence
- $n=1: 2^1 - 1 = 1$
- $n=2: 2^2 - 1 = 3$
- $n=3: 2^3 - 1 = 7$
- $n=4: 2^4 - 1 = 15$

---

## 3. The "Aha!" Moment
In binary, a Mersenne number is represented as a string of all `1`s.
- $3 = 11_2$
- $7 = 111_2$
- $15 = 1111_2$
You can calculate $2^n$ using bit-shifting: `(1LL << n)`.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy: Bit Shifting
 * Efficiency: Time O(1) per number
 */
void printMersenneNumbers(int count) {
    for (int n = 1; n <= count; n++) {
        // (1 << n) is 2^n
        unsigned long long val = (1ULL << n) - 1;
        std::cout << "M(" << n << ") = " << val << std::endl;
    }
}

int main() {
    printMersenneNumbers(10);
    return 0;
}
```
