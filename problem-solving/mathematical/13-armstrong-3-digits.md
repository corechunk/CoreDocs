# 13 | Armstrong Number (3 Digits)

Check if a 3-digit number is an Armstrong number.

---

## 1. The Objective
A 3-digit number is an **Armstrong number** if the sum of the cubes of its digits equals the number itself.
- **Example:** $153 = 1^3 + 5^3 + 3^3 = 1 + 125 + 27 = 153$.

---

## 2. Visual Logic
### Tracing 371
1. `3^3 = 27`
2. `7^3 = 343`
3. `1^3 = 1`
4. `Sum = 27 + 343 + 1 = 371`
5. `371 == 371 -> YES`

---

## 3. The "Aha!" Moment
Use the "Extract and Peel" loop (from Sum of Digits) but cube each digit before adding it to the sum.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy: Standard Digit Extraction
 */
bool isArmstrong3Digit(int n) {
    int original = n;
    int sum = 0;
    
    while (n > 0) {
        int digit = n % 10;
        sum += (digit * digit * digit);
        n /= 10;
    }
    
    return original == sum;
}

int main() {
    int num = 153;
    
    if (isArmstrong3Digit(num)) {
        std::cout << num << " is an Armstrong number." << std::endl;
    } else {
        std::cout << num << " is NOT an Armstrong number." << std::endl;
    }
    
    return 0;
}
```
