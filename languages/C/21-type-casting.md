# 🟢 Standard: Type Casting [CORE]

## Definition
Casting is the process of converting a variable from one data type to another. **Implicit** (automatic) casting is done by the compiler, while **Explicit** (manual) casting is forced by the programmer.

## 1. Legacy Way (C99 / C11 / C17)
Standard C-style cast syntax `(type)`.

```c
#include <stdio.h>

int main() {
    int a = 10, b = 3;
    
    // Explicit Cast: Force float math
    float result = (float)a / b; 
    
    printf("Result: %.2f\n", result); // Output: Result: 3.33
    return 0;
}
```

## 2. Modern Way (C23)
Same syntax, but often used to resolve ambiguities created by `auto`.

```c
#include <stdio.h> // Required for printf

int main() {
    auto a = 10;
    auto b = 3;
    
    // Mirror: Explicit cast to force float precision
    auto result = (float)a / b; 
    
    printf("Result: %.2f\n", result); // Output: Result: 3.33
    return 0;
}
```

# The Logic Bridge
// Logic: Casting doesn't change the underlying bits in memory; it tells the CPU which instruction to use (e.g., `CVTSI2SS` to convert integer bits to float bits) when loading the value into a register.
