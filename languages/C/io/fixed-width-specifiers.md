# 🟢 Standard: Fixed-Width Formatting [CORE]

## Definition
Fixed-width types from `<stdint.h>` require matching formatting macros from `<inttypes.h>`. This guarantees correct register size interpretation across different CPU registers (32-bit vs. 64-bit) during printing and scanning operations.

## 1. Legacy Way (C99)
In legacy formatting, using standard integer specifiers like `%d` or `%X` on fixed-width 64-bit types causes compiler warnings and garbage data representation due to register size mismatches.

```c
#include <stdio.h>
#include <stdint.h>

int main() {
    uint64_t a = 0b01;
    
    // Shift loop demonstrating register limits
    for (int i = 0; i < 64; i++) {
        a = a << 1;
        // WARNING / SCRAMBLE: %d expects 32-bit registers, causing overflow or truncation
        // printf("A: %d\n", a); 
    }
    return 0;
}
```

## 2. Modern Way (C23 / C11 / C17)
The system relies on platform-agnostic format macro strings from `<inttypes.h>` that prefix operations with `PRI` (print) or `SCN` (scan), followed by the specifier character and bit-width.

```c
#include <stdio.h>
#include <stdint.h>
#include <inttypes.h> // REQUIRED

int main() {
    uint64_t a = 0b01;
    int64_t b = 0b01;

    // Demonstration of Two's Complement shift comparison
    for (int i = 0; i < 63; i++) {
        a = a << 1;
        b = b << 1;
    }

    // Unsigned vs Signed decimal representation
    printf("Unsigned 64-bit Dec: %" PRIu64 "\n", a); // Output: 9223372036854775808
    printf("Signed 64-bit Dec:   %" PRId64 "\n", b); // Output: -9223372036854775808

    // Hexadecimal output shows IDENTICAL bits in memory
    printf("Unsigned Hex: %" PRIX64 "\n", a); // Output: 8000000000000000
    printf("Signed Hex:   %" PRIX64 "\n", b); // Output: 8000000000000000
    return 0;
}
```

## Deep-Dive Reference
* **Anatomy of `PRIX64` / `SCNd32`**:
  - **Prefix (`PRI` / `SCN`)**: Print (`printf`) or Scan (`scanf`).
  - **Specifier (`d`, `u`, `X`, `x`)**: Decimal, unsigned, uppercase hex, lowercase hex.
  - **Bit-Width (`8`, `16`, `32`, `64`)**: Matches standard hardware type sizes.
* **Two's Complement & Hex Memory Representation**:
  - The signed 64-bit value `-9223372036854775808` and unsigned `9223372036854775808` share the exact same raw bit array representation in hardware memory: a single `1` followed by sixty-three `0`s.
  - **Hex (`%X` / `PRIX64`)** prints the raw underlying bit pattern directly. It does *not* display sign symbols (`-`).
  - **Decimal (`%d` / `PRId64`)** applies mathematical interpretation rules, interpreting the leading sign bit to display negative representations.

# The Logic Bridge
// Logic: During preprocessing, macros like `PRIX64` expand to standard string literals (e.g., `"llX"` or `"lX"` depending on the compiler target arch). Adjacent string literals are automatically concatenated by the compiler into a single formatting string prior to compilation.
