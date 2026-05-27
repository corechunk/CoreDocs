# 71 | Power of Two Check

Check if a number is exactly a power of two ($2^n$).

---

## 1. The Objective
Given `16`, return `true`. Given `18`, return `false`.

---

## 2. Visual Logic
### The "Only One Bit" Property
In binary, a power of two always has exactly **one** bit set to `1`.
- `8`  = `1000`
- `16` = `10000`
- `32` = `100000`

---

## 3. The "Aha!" Moment
If you subtract 1 from a power of two, all bits to the right flip.
- `8` (1000) - `1` = `7` (0111)
- `8 & 7` = `1000 & 0111` = **0**.
Any non-power of two will result in a non-zero value.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy: Bitwise AND Trick
 * Efficiency: Time O(1)
 */
bool isPowerOfTwo(long long n) {
    // 0 is not a power of 2
    if (n <= 0) return false;
    
    return (n & (n - 1)) == 0;
}

int main() {
    int x = 64;
    if (isPowerOfTwo(x)) std::cout << x << " is a Power of Two." << std::endl;
    return 0;
}
```
