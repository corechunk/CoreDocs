# 🟢 Standard: Data Types [CORE]

## Definition
Types define the size and interpretation of bits in memory. This mirror shows the fundamental types and the shift of Boolean logic from a library to a native keyword.

## 1. Legacy Way (C99 / C11 / C17)
Standard primitives and library-based Boolean/Fixed-width support.

```c
#include <stdio.h>
#include <stdbool.h> // REQUIRED for bool (Same for C11/C17)

int main() {
    int i = 10;
    float f = 3.14f;
    double d = 3.14159;
    char c = 'A';
    bool b = true;
    char* s = "Hello"; // C-String (Pointer to char array)

    printf("Int: %d\n", i);      // Output: Int: 10
    printf("Float: %.2f\n", f);  // Output: Float: 3.14
    printf("Double: %.5f\n", d); // Output: Double: 3.14159
    printf("Char: %c\n", c);     // Output: Char: A
    printf("Bool: %d\n", b);     // Output: Bool: 1
    printf("Str: %s\n", s);      // Output: Str: Hello
    return 0;
}
```

## 2. Modern Way (C23)
Fundamental types are now more native, including Boolean logic and type inference.

```c
#include <stdio.h> // Required for printf

int main() {
    // Native Keywords: NO header required for bool, true, false, auto
    int i = 10;
    float f = 3.14f;
    double d = 3.14159;
    char c = 'A';
    bool b = true;      // Native keyword
    char* s = "Hello"; 

    auto count = i;     // Native keyword: auto-infers 'int'

    printf("Int: %d\n", i);      // Output: Int: 10
    printf("Float: %.2f\n", f);  // Output: Float: 3.14
    printf("Double: %.5f\n", d); // Output: Double: 3.14159
    printf("Char: %c\n", c);     // Output: Char: A
    printf("Bool: %d\n", b);     // Output: Bool: 1
    printf("Str: %s\n", s);      // Output: Str: Hello
    printf("Auto: %d\n", count); // Output: Auto: 10
    return 0;
}
```

## Deep-Dive Reference
For exhaustive width variants and memory layouts:
- [Integers](./data-type/integers.md) | [Floating Point](./data-type/floats.md) | [Fixed-Width](./data-type/fixed-width.md) | [Special Types](./data-type/special-types.md)

# The Logic Bridge
// Logic: C23 simplifies development by making Booleans (bool) and Type Inference (auto) native to the language syntax rather than relying on standard library macros.
