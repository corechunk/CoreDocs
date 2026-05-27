# 80 | Bit Counting (Set Bits)

Count how many `1`s are in the binary representation of a number.

---

## 1. The Objective
Given `7` (Binary `111`), return `3`. Given `8` (Binary `1000`), return `1`.

---

## 2. Visual Logic
### Method 1: The Shift Check
1. Check last bit (`n & 1`).
2. Shift right (`n >>= 1`).
3. Repeat until 0.

### Method 2: Kernighan’s Algorithm (Pro)
1. `n = n & (n - 1)`
This operation **always** clears the rightmost set bit.
- `7` (0111) & `6` (0110) = `6` (0110)  [1 bit cleared]
- `6` (0110) & `5` (0101) = `4` (0100)  [1 bit cleared]
- `4` (0100) & `3` (0011) = `0` (0000)  [1 bit cleared]
**Total:** 3 steps.

---

## 3. The "Aha!" Moment
Kernighan's algorithm is $O(\text{set\_bits})$ instead of $O(\text{total\_bits})$. It only iterates as many times as there are 1s.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy A: Kernighan’s Algorithm
 * Efficiency: Time O(set_bits)
 */
int countSetBits(int n) {
    int count = 0;
    while (n > 0) {
        n = n & (n - 1);
        count++;
    }
    return count;
}

int main() {
    int num = 125; // Binary: 1111101
    std::cout << "Set bits in " << num << ": " << countSetBits(num) << std::endl;
    return 0;
}
```
