# 45 | Disarium Number

Check if the sum of digits raised to the power of their position equals the number.

---

## 1. The Objective
A number is **Disarium** if the sum of its digits raised to the power of their respective positions is equal to the number itself.
- **Example:** $175$
- Position 1: $1^1 = 1$
- Position 2: $7^2 = 49$
- Position 3: $5^3 = 125$
- Sum: $1 + 49 + 125 = 175$. (Disarium!)

---

## 2. Visual Logic
### Tracing 89
1. Digits: 8, 9. Positions: 1, 2.
2. $8^1 = 8$
3. $9^2 = 81$
4. $8 + 81 = 89$. (YES)

---

## 3. The "Aha!" Moment
You need to know the **position** from left to right. 
1. Count total digits first.
2. While extracting digits (right to left), the position is `(total_digits - count)`.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <cmath>

/**
 * Strategy: Positional Powers
 */
bool isDisarium(int n) {
    int temp = n;
    int count = 0;
    while (temp > 0) { temp /= 10; count++; }
    
    int sum = 0;
    temp = n;
    int pos = count; // Start from the rightmost position
    while (temp > 0) {
        int digit = temp % 10;
        sum += pow(digit, pos);
        temp /= 10;
        pos--;
    }
    
    return sum == n;
}

int main() {
    int num = 175;
    if (isDisarium(num)) std::cout << num << " is a Disarium number." << std::endl;
    return 0;
}
```
