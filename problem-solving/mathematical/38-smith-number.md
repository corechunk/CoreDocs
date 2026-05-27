# 38 | Smith Number

Check if the sum of digits equals the sum of digits of its prime factors.

---

## 1. The Objective
A **Smith Number** is a composite number where the sum of its digits equals the sum of the digits of its prime factors.
- **Example:** $648$.
- Sum of digits: $6 + 4 + 8 = 18$.
- Prime factors: $2, 2, 2, 3, 3, 3, 3$.
- Sum of digits of factors: $2+2+2+3+3+3+3 = 18$.
- $18 == 18$. (Smith!)

---

## 2. Visual Logic
### Tracing 22
- Sum of digits: $2 + 2 = 4$.
- Factors: $2, 11$.
- Sum of digits of factors: $2 + (1+1) = 4$.
- $4 == 4$. (Smith!)

---

## 3. The "Aha!" Moment
This problem integrates **Sum of Digits** (Problem 10) and **Prime Factors** (Problem 25).
**Key:** When summing digits of prime factors, remember that a factor like `11` contributes `1+1`, not `11`.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

int sumDigits(int n) {
    int sum = 0;
    while (n > 0) {
        sum += (n % 10);
        n /= 10;
    }
    return sum;
}

/**
 * Strategy: Dual Sum Comparison
 */
bool isSmith(int n) {
    // Smith numbers must be composite (not prime)
    bool isPrime = true;
    for (int i = 2; i * i <= n; i++) {
        if (n % i == 0) { isPrime = false; break; }
    }
    if (isPrime) return false;

    int originalSum = sumDigits(n);
    int factorSum = 0;
    int temp = n;

    // Standard prime factorization loop
    for (int i = 2; i * i <= temp; i++) {
        while (temp % i == 0) {
            factorSum += sumDigits(i);
            temp /= i;
        }
    }
    if (temp > 1 && temp != n) {
        factorSum += sumDigits(temp);
    }

    return originalSum == factorSum;
}

int main() {
    int num = 648;
    if (isSmith(num)) std::cout << num << " is a Smith number." << std::endl;
    return 0;
}
```
