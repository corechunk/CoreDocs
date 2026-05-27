# 05 | Even or Odd (No Modulo)

Determine if a number is even or odd without using the `%` operator.

---

## 1. The Objective
The standard way is `if (n % 2 == 0)`. But how can you do it if `%` is forbidden or if you want to be faster?

---

## 2. Visual Logic
### Method 1: Bitwise (The "CPU" Way)
In binary, every even number ends in `0` and every odd number ends in `1`.
- `4` = `100` (Even)
- `5` = `101` (Odd)
- `6` = `110` (Even)

If we perform a **Bitwise AND** with `1`, we only get the last bit.

### Method 2: Division/Multiplication
Divide by 2, then multiply by 2. If you get the original number, it was even.
- `5 / 2 = 2` (Integer division)
- `2 * 2 = 4` (Not 5, so it was Odd)

---

## 3. The "Aha!" Moment
The last bit of a number determines its "parity" (evenness). The `&` operator is often faster than `%` at the hardware level.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy A: Bitwise AND
 * Efficiency: Time O(1) - Extremely fast
 */
bool isEvenBitwise(int n) {
    // If the last bit is 0, the number is even.
    // (n & 1) returns 1 for odd, 0 for even.
    return !(n & 1);
}

/**
 * Strategy B: Division Logic
 * Efficiency: Time O(1)
 */
bool isEvenDivision(int n) {
    return (n / 2) * 2 == n;
}

int main() {
    int num;
    std::cout << "Enter a number: ";
    std::cin >> num;
    
    if (isEvenBitwise(num)) {
        std::cout << num << " is EVEN (via Bitwise)." << std::endl;
    } else {
        std::cout << num << " is ODD (via Bitwise)." << std::endl;
    }
    
    if (isEvenDivision(num)) {
        std::cout << num << " is EVEN (via Division)." << std::endl;
    } else {
        std::cout << num << " is ODD (via Division)." << std::endl;
    }
    
    return 0;
}
```
