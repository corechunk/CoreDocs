# 62 | Narcissistic Number

Check if the sum of digits raised to the power of the number of digits equals the number.

---

## 1. The Objective
A **Narcissistic Number** (or Pluperfect Digital Invariant) is a number that is the sum of its own digits each raised to the power of the number of digits.
- **Note:** This is identical to the general Armstrong Number (Problem 14).
- **Example:** $370$ (3 digits)
- $3^3 + 7^3 + 0^3 = 27 + 343 + 0 = 370$.

---

## 2. Visual Logic
### Tracing 9474 (4 digits)
1. $9^4 = 6561$
2. $4^4 = 256$
3. $7^4 = 2401$
4. $4^4 = 256$
5. Sum: $6561 + 256 + 2401 + 256 = 9474$. (YES)

---

## 3. The "Aha!" Moment
Like the Armstrong check, the "Narcissism" comes from the power being exactly the count of digits.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <cmath>
#include <vector>

/**
 * Strategy: Multi-pass Digit extraction
 */
bool isNarcissistic(long long n) {
    std::vector<int> digits;
    long long temp = n;
    while (temp > 0) {
        digits.push_back(temp % 10);
        temp /= 10;
    }
    
    int p = digits.size();
    long long sum = 0;
    for (int d : digits) {
        sum += pow(d, p);
    }
    
    return sum == n;
}

int main() {
    long long num = 9474;
    if (isNarcissistic(num)) std::cout << num << " is Narcissistic." << std::endl;
    return 0;
}
```
