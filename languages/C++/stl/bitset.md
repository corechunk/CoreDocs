# 🔢 STL Bitset - Master Reference

## 1. The Objective
`std::bitset` is a specialized container that stores bits (elements with only two possible values: 0 or 1). It is optimized for space efficiency and provides a high-level API for bit manipulation, making it superior to raw bit-masking in many cases.

---

## 2. Visual Logic
### Fixed-Size Bit Array
```text
[ 0 | 1 | 0 | 1 | 1 | 0 | 0 | 1 ] (Size: 8)
  7   6   5   4   3   2   1   0  (Indices)
```

---

## 3. # The Logic Bridge (Key Points)

- **Static Size:** Unlike `vector<bool>`, a `bitset`'s size is fixed at compile-time (`std::bitset<32>`).
- **Memory Optimization:** It uses exactly 1 bit per element. A `vector<bool>` is also specialized for space, but `bitset` provides faster bitwise logic operators (`&`, `|`, `^`, `<<`).
- **String/Int Conversion:** `bitset` can easily convert between raw binary strings and integer values, making it perfect for debugging hardware flags or network protocols.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Exhaustive Usage)

```cpp
#include <iostream>
#include <bitset>
#include <string>

int main() {
    // --- 1. INITIALIZATION ---
    std::bitset<8> b1;                    // 00000000
    std::bitset<8> b2(42);                // 00101010 (From integer)
    std::bitset<8> b3("1100");            // 00001100 (From string)

    // --- 2. BIT MANIPULATION ---
    b1.set(1);                            // Set index 1 to 1
    b1.reset(1);                          // Set index 1 to 0
    b1.flip(0);                           // Toggle index 0
    b1.set();                             // Set all bits to 1
    b1.reset();                           // Set all bits to 0

    // --- 3. QUERIES ---
    bool b = b2.test(3);                  // Safe access to index 3
    bool any = b2.any();                  // Is any bit 1?
    bool none = b2.none();                // Are all bits 0?
    size_t count = b2.count();            // Number of 1s

    // --- 4. CONVERSIONS ---
    std::string s = b2.to_string();       // "00101010"
    unsigned long n = b2.to_ulong();      // 42

    // --- 5. BITWISE LOGIC ---
    auto b4 = b2 & b3;                    // AND
    auto b5 = b2 | b3;                    // OR
    
    std::cout << "Bitset b2: " << b2 << std::endl;

    return 0;
}
```

---
[➔ Back to STL Hub](00-stl-overview.md)
