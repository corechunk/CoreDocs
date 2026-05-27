# 99 | Magic Number

Check if the recursive sum of digits eventually reaches 1.

---

## 1. The Objective
A number is a **Magic Number** if the sum of its digits is calculated repeatedly until a single digit is obtained, and that digit is **1**.
- **Example:** $1729$.
- $1+7+2+9 = 19$.
- $1+9 = 10$.
- $1+0 = 1$. (Magic!)

---

## 2. Visual Logic
### The "Digital Root" Path
$199 \to 1+9+9 = 19 \to 1+9 = 10 \to 1+0 = 1$.

---

## 3. The "Aha!" Moment
The final single digit (digital root) can be found using the **Modulo 9** property:
$\text{DigitalRoot}(n) = 1 + (n-1) \pmod 9$.
If the result is 1, the number is Magic.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy: Iterative Summation
 */
bool isMagic(int n) {
    int sum = n;
    while (sum > 9) {
        int tempSum = 0;
        while (sum > 0) {
            tempSum += (sum % 10);
            sum /= 10;
        }
        sum = tempSum;
    }
    return sum == 1;
}

int main() {
    int num = 1729;
    if (isMagic(num)) std::cout << num << " is a Magic number." << std::endl;
    return 0;
}
```
