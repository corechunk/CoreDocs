# 🟢 Standard: Variables & Constants [CORE]

## Definition
Variables are mutable storage locations in memory. Constants are immutable values. This file mirrors how C23 moves constant logic from the Preprocessor/RAM into the Compiler's core logic.

## 1. Legacy Way (C99 / C11 / C17)
Constants require `#define` (text replacement) or `const` (read-only RAM).

```c
#include <stdio.h>

#define MAX_VAL 100 // Preprocessor: No type safety

int main() {
    const int buffer = 512; // Read-only variable in RAM
    int score = 0;          // Mutable variable
    
    printf("Max: %d\n", MAX_VAL);    // Output: Max: 100
    printf("Buffer: %d\n", buffer);  // Output: Buffer: 512
    printf("Score: %d\n", score);    // Output: Score: 0
    return 0;
}
```

## 2. Modern Way (C23)
C23 introduces `constexpr` for true type-safe compile-time constants.

```c
#include <stdio.h> // Required for printf

int main() {
    // constexpr: Native keyword. No header required.
    // True compile-time constant (Typed replacement for #define)
    constexpr int MAX_VAL = 100; 

    // Legacy const and variables still work
    const int buffer = 512; 
    int score = 0;

    printf("Max: %d\n", MAX_VAL);    // Output: Max: 100
    printf("Buffer: %d\n", buffer);  // Output: Buffer: 512
    printf("Score: %d\n", score);    // Output: Score: 0
    return 0;
}
```

# The Logic Bridge
// Logic: `constexpr` allows the compiler to calculate values at compile-time and enforce types, whereas `#define` just swaps text before the compiler even starts.
