# 🔴 Standard: Floating Point [SYSTEMS]

## Definition
Decimals are represented using the IEEE 754 standard (Sign, Exponent, Mantissa). Mirroring precision levels and C23 Hex-float support.

## 1. Legacy Way (C99 / C11 / C17)
Standard floating point types.

```c
#include <stdio.h>

int main() {
    float f = 3.14f;    // 4 bytes
    double d = 3.14159; // 8 bytes
    
    printf("Float: %.2f\n", f);  // Output: Float: 3.14
    printf("Double: %.5f\n", d); // Output: Double: 3.14159
    return 0;
}
```

## 2. Modern Way (C23)
Supports modern hexadecimal floating-point literals for bit-exact precision.

```c
#include <stdio.h>

int main() {
    float f = 3.14f;
    double d = 3.14159;
    
    // Hexadecimal floating point (C23)
    double hex_f = 0x1.p+3; // 1.0 * 2^3 = 8.0
    
    printf("Float: %.2f\n", f);      // Output: Float: 3.14
    printf("Hex Float: %.1f\n", hex_f); // Output: Hex Float: 8.0
    return 0;
}
```

# The Logic Bridge
// Logic: Floating point "Precision" is limited by the number of bits in the mantissa; `double` is the professional default because it minimizes rounding errors compared to `float`.
