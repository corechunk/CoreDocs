# 🔴 Standard: Bitwise Operators [SYSTEMS]

## Definition
Low-level bit manipulation: `&` (AND), `|` (OR), `^` (XOR), `~` (NOT), and shifts `<<`, `>>`.

## 1. Legacy Way (C++11 / C++17)
Using Hex literals.

```cpp
#include <iostream>

int main() {
    int a = 0x0C; // 1100
    int b = 0x0A; // 1010
    std::cout << (a & b) << "\n"; // Output: 8
    return 0;
}
```

## 2. Modern Way (C23)
Using Binary literals.

```cpp
#include <iostream>

int main() {
    auto a = 0b1100;
    auto b = 0b1010;
    std::cout << (a & b) << "\n"; // Output: 8
    return 0;
}
```

# The Logic Bridge
// Logic: Bitwise operators are direct ALU instructions. Shift left (`<<`) is effectively a fast multiplication by powers of 2.
