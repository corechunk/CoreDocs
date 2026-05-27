# 40 | Amicable Numbers (Friendly Pairs)

Check if two numbers are amicable.

---

## 1. The Objective
Two numbers $a$ and $b$ are **Amicable** if the sum of proper divisors of $a$ equals $b$, AND the sum of proper divisors of $b$ equals $a$.
- **Example:** $220$ and $284$.
- Proper divisors of 220: Sum = **284**.
- Proper divisors of 284: Sum = **220**.

---

## 2. Visual Logic
### The "Bridge" Strategy
1. Calculate $\text{SumOfProperDivisors}(a) \to \text{Result1}$.
2. Calculate $\text{SumOfProperDivisors}(b) \to \text{Result2}$.
3. If $(\text{Result1} == b)$ AND $(\text{Result2} == a)$, they are friends!

---

## 3. The "Aha!" Moment
Reuse the **Sum of Divisors** logic (Problem 32). Remember that "Proper" divisors exclude the number itself, so subtract the number from the total sum.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Helper: Sum of proper divisors
 */
int sumProperDivisors(int n) {
    int sum = 1; // 1 is always a proper divisor
    for (int i = 2; i * i <= n; i++) {
        if (n % i == 0) {
            sum += i;
            if (i * i != n) sum += (n / i);
        }
    }
    return sum;
}

/**
 * Strategy: Dual Sum Verification
 */
bool areAmicable(int a, int b) {
    return (sumProperDivisors(a) == b) && (sumProperDivisors(b) == a);
}

int main() {
    int x = 220, y = 284;
    if (areAmicable(x, y)) {
        std::cout << x << " and " << y << " are Amicable numbers." << std::endl;
    }
    return 0;
}
```
