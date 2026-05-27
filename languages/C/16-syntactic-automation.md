# 🔴 Standard: Syntactic Automation [SYSTEMS]

## Definition
Syntactic automation uses the Preprocessor to "write code for you." This allows for type-generic logic (macros) and templates that adapt to different data types during compilation.

## 1. Legacy Way (C99)
Standard `#define` macros for simple logic.

```c
#include <stdio.h>

// Simple macro: No type safety
#define MAX(a, b) ((a) > (b) ? (a) : (b))

int main() {
    int i = 10, j = 20;
    float x = 5.5, y = 2.2;
    
    printf("Max Int: %d\n", MAX(i, j));     // Output: Max Int: 20
    printf("Max Float: %.1f\n", MAX(x, y)); // Output: Max Float: 5.5
    return 0;
}
```

## 2. Modern Way (C23)
Using `_Generic` (C11/C23) and `auto` to create type-safe, automated selection logic.

```c
#include <stdio.h>

// Type-safe automated selection (C11/C23 Native)
#define GET_TYPE_NAME(x) _Generic((x), \
    int: "Integer", \
    float: "Float", \
    default: "Unknown" \
)

int main() {
    auto i = 10;   // Inferred as int
    auto f = 5.5f; // Inferred as float
    
    printf("i is: %s\n", GET_TYPE_NAME(i)); // Output: i is: Integer
    printf("f is: %s\n", GET_TYPE_NAME(f)); // Output: f is: Float
    return 0;
}
```

# The Logic Bridge
// Logic: The Preprocessor performs text substitution before the compiler starts. `_Generic` takes this further by allowing the compiler to choose a specific code path based on the *type* of the expression during the translation phase.
