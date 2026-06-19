# 🟢 Standard: Data Types [CORE]

## Definition
Types define the size and bit-level interpretation of memory space. In addition to standard integer and float primitives, strings exist as a library convention (`char[]` / `char*` with a null-terminator), and boolean logic has transitioned from library macros to native keyword definitions.

## 1. Legacy Way (C99 / C11 / C17)
* Primitives require library headers (`stdbool.h` for `bool`, `stdint.h` for fixed-width types).
* Strings are pointer arrays initialized via character literals or raw stack arrays.

```c
#include <stdio.h>
#include <stdbool.h> // Required for bool

int main() {
    int i = 10;
    float f = 3.14f;
    bool b = true;
    char* s = "Hello"; // String pointer to read-only memory
    char arr[] = "Stack"; // String array on stack (Read-Write)

    printf("Bool: %d\n", b);
    printf("Str: %s\n", s);
    return 0;
}
```

## 2. Modern Way (C23)
* Booleans (`bool`, `true`, `false`) are native keywords requiring no headers.
* Type inference using `auto` allows the compiler to deduce primitive types automatically at compile time.

```c
#include <stdio.h>

int main() {
    int i = 10;
    float f = 3.14f;
    bool b = true; // Native keyword, no header
    char* s = "Hello";

    auto inferred_int = i; // Infers int

    printf("Bool: %d\n", b);
    printf("Str: %s\n", s);
    return 0;
}
```

## Deep-Dive Reference
For exhaustive analysis of individual structures, ranges, and sizes:
- [Integers](./data-type/integers.md) | [Floating Point](./data-type/floats.md) | [Fixed-Width](./data-type/fixed-width.md) | [Special Types](./data-type/special-types.md) | [String Handling](../14-string-handling.md)

# The Logic Bridge
// Logic: Primitive variables map directly to CPU registers and memory width boundaries, while C-strings are not native data types but structured sequences mapped linearly in memory.
