# 34 | Abundant & Deficient Numbers

Classify numbers based on the sum of their proper divisors.

---

## 1. The Objective
Compare the sum of proper divisors (excluding the number itself) with the number $n$.
- **Perfect:** $\text{Sum} == n$.
- **Abundant:** $\text{Sum} > n$.
- **Deficient:** $\text{Sum} < n$.

---

## 2. Visual Logic
### Tracing 12
- Proper divisors: 1, 2, 3, 4, 6.
- Sum: $1+2+3+4+6 = 16$.
- $16 > 12$. Result: **ABUNDANT**.

---

## 3. The "Aha!" Moment
Calculate the sum of all divisors (Problem 32) and then subtract $n$ to get the "Proper Sum."

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

int getProperSum(int n) {
    int sum = 0;
    for (int i = 1; i * i <= n; i++) {
        if (n % i == 0) {
            sum += i;
            if (i * i != n && i != 1) { // i=1 handled separately for proper sum
                sum += (n / i);
            }
        }
    }
    // Proper sum excluding the number itself
    return sum - n;
}

void classifyNumber(int n) {
    int sum = getProperSum(n) + 1; // Re-add 1 because our loop logic needs adjustment for proper sum
    // Better way: 
    int total_sum = 0;
    for (int i = 1; i * i <= n; i++) {
        if (n % i == 0) {
            total_sum += i;
            if (i * i != n) total_sum += (n / i);
        }
    }
    int proper_sum = total_sum - n;

    if (proper_sum == n) std::cout << n << " is Perfect." << std::endl;
    else if (proper_sum > n) std::cout << n << " is Abundant." << std::endl;
    else std::cout << n << " is Deficient." << std::endl;
}

int main() {
    classifyNumber(12);
    classifyNumber(6);
    classifyNumber(8);
    return 0;
}
```
