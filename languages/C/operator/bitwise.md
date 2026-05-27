# 🔴 Standard: Bitwise Operators [SYSTEMS]

## Definition
Operators that manipulate data at the individual bit level. Crucial for hardware control, flags, and efficiency.

## 1. Legacy Way (C99 / C11 / C17)
Using Hex literals for bitwise clarity.

```c
#include <stdio.h>

int main() {
    int a = 0x0A; // Binary: 1010
    int b = 0x03; // Binary: 0011
    
    printf("AND: %d\n", a & b); // Output: AND: 2 (0010)
    printf("XOR: %d\n", a ^ b); // Output: XOR: 9 (1001)
    printf("SHIFT: %d\n", a << 1); // Output: SHIFT: 20 (10100)
    return 0;
}
```

## 2. Modern Way (C23)
Mirroring the same tasks using C23 native binary literals.

```c
#include <stdio.h> // Required for printf

int main() {
    // Native Binary Literals
    int a = 0b1010; 
    int b = 0b0011;
    
    printf("AND: %d\n", a & b);    // Output: AND: 2
    printf("XOR: %d\n", a ^ b);    // Output: XOR: 9
    printf("SHIFT: %d\n", a << 1); // Output: SHIFT: 20
    return 0;
}
```

# The Logic Bridge
// Logic: Bitwise operators map 1-to-1 with CPU logic gates (`AND`, `XOR`, `SHL`). They are the fastest operations a computer can perform.
