# 06 | Swap Two Numbers (No Temp)

Swap the values of two variables without using a third temporary variable.

---

## 1. The Objective
Given `a = 5` and `b = 10`, change them so that `a = 10` and `b = 5`.

---

## 2. Visual Logic
### Method 1: Addition/Subtraction
1. `a = a + b` (Now `a` holds the sum: 15)
2. `b = a - b` (Sum - old `b` = old `a`: 5. Now `b` is 5)
3. `a = a - b` (Sum - new `b` = old `b`: 10. Now `a` is 10)

### Method 2: Bitwise XOR (The "Pure Logic" Way)
XOR is reversible. 
1. `a = a ^ b`
2. `b = a ^ b` (Original `b` is cancelled out, `b` becomes original `a`)
3. `a = a ^ b` (New `b` is original `a`, cancelling it out, `a` becomes original `b`)

---

## 3. The "Aha!" Moment
Variables are just containers. If you can store the "relationship" between two numbers (their sum or their XOR difference) in one container, you can use it to reconstruct the other.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy A: Addition and Subtraction
 * Note: Risk of overflow if a + b exceeds type limits!
 */
void swapMath(int &a, int &b) {
    a = a + b;
    b = a - b;
    a = a - b;
}

/**
 * Strategy B: Bitwise XOR
 * Note: Safest way (no overflow) and very fast.
 */
void swapXOR(int &a, int &b) {
    if (&a == &b) return; // Cannot XOR a variable with itself
    a = a ^ b;
    b = a ^ b;
    a = a ^ b;
}

int main() {
    int x = 5, y = 10;
    
    std::cout << "Original: x=" << x << ", y=" << y << std::endl;
    
    swapMath(x, y);
    std::cout << "After Math Swap: x=" << x << ", y=" << y << std::endl;
    
    swapXOR(x, y);
    std::cout << "After XOR Swap: x=" << x << ", y=" << y << std::endl;
    
    return 0;
}
```
