# 🔢 Bit Manipulation

## 1. The Objective
Bit Manipulation is the act of algorithmically manipulating bits or other pieces of data shorter than a word. Computer programming tasks that require bit manipulation include low-level device control, error detection/correction, and high-performance algorithms.

---

## 2. Visual Logic
### Standard Operations
```text
A: 1010 (10)
B: 1100 (12)

AND (&): 1000 (8)  - Keep only common bits
OR  (|): 1110 (14) - Combine all bits
XOR (^): 0110 (6)  - Keep only different bits
```

---

## 3. The Logic Bridge
- **Binary as Sets:** Think of a 32-bit integer as a **Set** of numbers $\{0, 1, 2, ..., 31\}$. A bit is `1` if that number is in the set. `AND` is Intersection, `OR` is Union, and `XOR` is Symmetric Difference.
- **The "Power of 2" Trick:** The expression `(n & (n - 1))` removes the lowest set bit. If the result is `0`, then `n` was a power of 2.
- **Masking:** Using `1 << k` creates a "Mask" to target only the $k$-th bit.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Bit Hacks)

```cpp
#include <iostream>

int main() {
    int n = 10; // 1010 in binary

    // 1. Check if k-th bit is set
    int k = 1;
    bool isSet = n & (1 << k);
    std::cout << "Bit 1 is set: " << isSet << std::endl;

    // 2. Count set bits (Brian Kernighan's Algorithm)
    int count = 0;
    int temp = n;
    while (temp > 0) {
        temp &= (temp - 1);
        count++;
    }
    std::cout << "Set bits in 10: " << count << std::endl;

    return 0;
}
```

---
[➔ Back to Roadmap](../DSA-Master-Roadmap.md)
