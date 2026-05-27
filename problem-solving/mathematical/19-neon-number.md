# 19 | Neon Number

Check if the sum of digits of the square of a number is equal to the number itself.

---

## 1. The Objective
A **Neon Number** is a number where the sum of digits of its square is equal to the number itself.
- **Example:** $9$.
- Square: $9^2 = 81$.
- Sum of digits of square: $8 + 1 = 9$.
- $9 == 9$. (Neon!)

---

## 2. Visual Logic
### Tracing 12
1. `12^2 = 144`
2. `Sum = 1 + 4 + 4 = 9`
3. `9 != 12`
4. Result: **NO**

---

## 3. The "Aha!" Moment
Square the number first, then run the **Sum of Digits** loop on the result of that square.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy: Square -> Sum Digits
 */
bool isNeon(int n) {
    long long square = 1LL * n * n;
    int sum = 0;
    
    while (square > 0) {
        sum += (square % 10);
        square /= 10;
    }
    
    return sum == n;
}

int main() {
    int num = 9;
    
    if (isNeon(num)) {
        std::cout << num << " is a Neon number." << std::endl;
    } else {
        std::cout << num << " is NOT a Neon number." << std::endl;
    }
    
    return 0;
}
```
