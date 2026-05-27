# 🔴 Standard: Integer Deep-Dive [SYSTEMS]

## Definition
The integer hierarchy manages the width (bits) of whole numbers. C23 adds binary literals and separators to the standard `short`, `int`, and `long long` types.

## 1. Legacy Way (C99 / C11 / C17)
Standard widths and Hex-based bitmasks. `long long` is native since C99.

```c
#include <stdio.h>
#include <limits.h> // Required for INT_MAX

int main() {
    short a = 10;      // 2 bytes
    int b = 100;       // 4 bytes
    long long c = 1000; // 8 bytes (Standard since C99)

    int mask = 0x0C; // Bitmask (Binary: 1100) using Hex

    printf("Types: %d, %d, %lld\n", a, b, c); // Output: Types: 10, 100, 1000
    printf("Mask: %d\n", mask);               // Output: Mask: 12
    printf("Max: %d\n", INT_MAX);             // Output: Max: 2147483647
    return 0;
}
```

## 2. Modern Way (C23)
Identical types, but with binary literals (`0b`) and digit separators (`_`) for bit-level clarity.

```c
#include <stdio.h>
#include <limits.h> // Still required for INT_MAX

int main() {
    short a = 10;
    int b = 100;
    long long c = 1_000_000; // Digit separator (C23)

    // Binary Literal (C23 Native - Mirrors Legacy Hex 0x0C)
    int mask = 0b1100; 

    printf("Types: %d, %d, %lld\n", a, b, c); // Output: Types: 10, 100, 1000000
    printf("Mask: %d\n", mask);               // Output: Mask: 12
    printf("Max: %d\n", INT_MAX);             // Output: Max: 2147483647
    return 0;
}
```

# The Logic Bridge
// Logic: C integers are just binary sequences; binary literals (`0b`) simply allow the programmer to write those bits directly instead of converting them to Decimal or Hex.
