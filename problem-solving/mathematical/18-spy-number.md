# 18 | Spy Number

Check if the sum of its digits equals the product of its digits.

---

## 1. The Objective
A **Spy Number** is a number where the sum of its digits is equal to the product of its digits.
- **Example:** $1124$.
- Sum: $1 + 1 + 2 + 4 = 8$.
- Product: $1 \times 1 \times 2 \times 4 = 8$.
- $8 == 8$. (Spy!)

---

## 2. Visual Logic
### Tracing 123
1. `Sum = 1 + 2 + 3 = 6`
2. `Prod = 1 * 2 * 3 = 6`
3. Result: **YES**

---

## 3. The "Aha!" Moment
Maintain two accumulators inside your digit extraction loop: `sum` (initialized to 0) and `product` (initialized to 1).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy: Concurrent Sum and Product Calculation
 */
bool isSpy(int n) {
    int sum = 0;
    int product = 1;
    
    while (n > 0) {
        int digit = n % 10;
        sum += digit;
        product *= digit;
        n /= 10;
    }
    
    return sum == product;
}

int main() {
    int num = 1124;
    
    if (isSpy(num)) {
        std::cout << num << " is a Spy number." << std::endl;
    } else {
        std::cout << num << " is NOT a Spy number." << std::endl;
    }
    
    return 0;
}
```
