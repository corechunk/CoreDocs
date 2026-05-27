# 🟢 Standard: Operators [CORE]

## Definition
C++ operators handle math, logic, and bitwise tasks. Unlike C, C++ allows for **Operator Overloading**, enabling custom types to use symbols like `+` and `-`.

## 1. Legacy Way (C++11 / C++17)
Standard usage of built-in operators.

```cpp
#include <iostream>

int main() {
    int a = 10, b = 3;
    bool res = (a > b);
    int bit = a & b; 

    std::cout << "Math: " << (a + b) << "\n"; // Output: Math: 13
    std::cout << "Bool: " << res << "\n";     // Output: Bool: 1
    return 0;
}
```

## 2. Modern Way (C23)
Using modern literals and the "Spaceship Operator" (`<=>`) for three-way comparisons.

```cpp
#include <iostream>
#include <compare> // C++20

int main() {
    auto a = 10, b = 3;
    
    // Spaceship Operator (<=>): Three-way comparison
    auto cmp = (a <=> b); 
    
    if (cmp > 0) std::cout << "A is Greater\n"; // Output: A is Greater
    
    // Binary literals (Modern)
    auto mask = 0b1010;
    std::cout << "Mask: " << mask << "\n"; // Output: Mask: 10
    return 0;
}
```

## Deep-Dive Reference
For exhaustive truth tables and overloading:
- [Mathematical](./operator/math.md) | [Logical](./operator/logical.md) | [Bitwise](./operator/bitwise.md) | [Assignment](./operator/assignment.md)

# The Logic Bridge
// Logic: Operators are lowered to CPU instructions. Overloaded operators are physically transformed into function calls (e.g., `a + b` becomes `a.operator+(b)`).
