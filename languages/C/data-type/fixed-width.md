# 🔴 Standard: Fixed-Width Types [SYSTEMS]

## Definition
Fixed-width types guarantee exact bit-counts across all hardware (Arduino, PC, Mainframe). Mirroring the exhaustive list from `stdint.h`.

## 1. Legacy Way (C99 / C11 / C17)
Requires `stdint.h` for portability.

```c
#include <stdio.h>
#include <stdint.h> // REQUIRED (Same for C11/C17)

int main() {
    int8_t   a = 127;                // 8-bit Signed
    int16_t  b = 32767;              // 16-bit Signed
    int32_t  c = 2147483647;         // 32-bit Signed
    int64_t  d = 9223372036854775807LL; // 64-bit Signed
    
    uint8_t  u_a = 255;              // 8-bit Unsigned
    uint32_t u_c = 0xFFFFFFFF;       // 32-bit Unsigned (Hex)

    printf("i8: %d, u8: %u\n", a, u_a); // Output: i8: 127, u8: 255
    printf("u32: %u\n", u_c);           // Output: u32: 4294967295
    return 0;
}
```

## 2. Modern Way (C23)
Same types, adding binary literals and C23 bit-precise integers.

```c
#include <stdio.h>
#include <stdint.h> // Still REQUIRED

int main() {
    int8_t   a = 127; 
    int16_t  b = 32767;
    int32_t  c = 2147483647;
    int64_t  d = 9_223_372_036_854_775_807LL; // Digit separators

    uint32_t u_c = 0b11111111_11111111_11111111_11111111; // Binary Mask
    
    // C23 bit-precise integer (Exactly 3 bits)
    _BitInt(3) tiny = 3; 

    printf("i8: %d, i64: %lld\n", a, d); // Output: i8: 127, i64: 9223372036854775807
    printf("u32: %u\n", u_c);            // Output: u32: 4294967295
    printf("Bit3: %d\n", (int)tiny);     // Output: Bit3: 3
    return 0;
}
```

# The Logic Bridge
// Logic: Fixed-width types are `typedef` aliases that the compiler maps to the correct internal type for the specific CPU, ensuring binary compatibility.
