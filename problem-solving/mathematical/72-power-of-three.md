# 72 | Power of Three Check

Check if a number is a power of three ($3^n$).

---

## 1. The Objective
Given `27`, return `true`. Given `30`, return `false`.

---

## 2. Visual Logic
### The "Repeated Division" Strategy
1. Keep dividing by 3 as long as the remainder is 0.
2. If you reach **1**, it was a power of three.

---

## 3. The "Aha!" Moment
Unlike powers of two, there is no simple bitwise trick for base 3. You must use iteration or a pre-calculated max-power constant check.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy: Iterative Division
 * Efficiency: Time O(log3 N)
 */
bool isPowerOfThree(int n) {
    if (n <= 0) return false;
    
    while (n % 3 == 0) {
        n /= 3;
    }
    
    return n == 1;
}

int main() {
    int x = 81;
    if (isPowerOfThree(x)) std::cout << x << " is a Power of Three." << std::endl;
    return 0;
}
```
