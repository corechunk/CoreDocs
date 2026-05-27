# 32 | Sum of Divisors

Calculate the sum of all divisors of $n$.

---

## 1. The Objective
Given `n = 12`, divisors are `1, 2, 3, 4, 6, 12`.
Sum = $1+2+3+4+6+12 = 28$.

---

## 2. Visual Logic
### Tracing (n=12)
- $\sqrt{12} \approx 3.46$
- $i=1$: (1, 12) -> Sum = 13
- $i=2$: (2, 6)  -> Sum = 13 + 8 = 21
- $i=3$: (3, 4)  -> Sum = 21 + 7 = 28
Final: **28**.

---

## 3. The "Aha!" Moment
Apply the $O(\sqrt{n})$ divisor logic and accumulate the values into a sum. This is the foundation for classifying numbers as Perfect, Abundant, or Deficient.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy: O(sqrt n) Accumulation
 */
long long sumOfDivisors(int n) {
    long long sum = 0;
    for (int i = 1; i * i <= n; i++) {
        if (n % i == 0) {
            sum += i;
            if (i * i != n) {
                sum += (n / i);
            }
        }
    }
    return sum;
}

int main() {
    int num = 12;
    std::cout << "Sum of divisors of " << num << ": " << sumOfDivisors(num) << std::endl;
    return 0;
}
```
