# 🟢 Standard: Operators [CORE]

## Definition
Operators are symbols that tell the compiler to perform specific mathematical, logical, or bitwise manipulations. This file acts as a mirrored hub for the core categories.

## 1. Legacy Way (C99 / C11 / C17)
Standard usage of symbols. Requires `stdbool.h` for logical tasks involving booleans.

```c
#include <stdio.h>
#include <stdbool.h> // REQUIRED for bool (C99-C17)

int main() {
    int a = 10, b = 3;
    bool is_equal = (a == b);
    int bit_and = a & b; // 1010 & 0011 = 0010 (2)

    printf("Math: %d\n", a + b);      // Output: Math: 13
    printf("Logical: %d\n", is_equal); // Output: Logical: 0
    printf("Bitwise: %d\n", bit_and);  // Output: Bitwise: 2
    return 0;
}
```

## 2. Modern Way (C23)
Identical symbols, but with native boolean support and modern literals.

```c
#include <stdio.h> // Required for printf

int main() {
    auto a = 10, b = 3;
    bool is_equal = (a == b); // Native keyword: No header
    int bit_and = a & b; 

    printf("Math: %d\n", a + b);      // Output: Math: 13
    printf("Logical: %d\n", is_equal); // Output: Logical: 0
    printf("Bitwise: %d\n", bit_and);  // Output: Bitwise: 2
    return 0;
}
```

## Deep-Dive Reference
For exhaustive truth tables and bitwise shifts:
- [Mathematical](./operator/math.md) | [Logical](./operator/logical.md) | [Bitwise](./operator/bitwise.md) | [Assignment](./operator/assignment.md)

# The Logic Bridge
// Logic: Operators are translated directly into CPU instructions (e.g., `ADD`, `SUB`, `AND`). The "Modern" change is purely syntactic (built-in types), while the raw machine logic remains the same.
