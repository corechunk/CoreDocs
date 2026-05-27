# 🟢 Standard: Truth Rule [CORE]

## Definition
In C, there is no separate "Truthiness" engine. Everything is evaluated based on **Zero Parity**: `0` is False, and **any non-zero value** (usually 1) is True.

## 1. Legacy Way (C99 / C11 / C17)
Logic evaluation using integers and library-based booleans.

```c
#include <stdio.h>
#include <stdbool.h> // REQUIRED

int main() {
    int x = 10;
    bool is_valid = (x != 0); // Explicit truth
    
    if (x) { // 10 is non-zero, so this is TRUE
        printf("X is True\n"); // Output: X is True
    }
    
    if (0) { /* This never runs */ }
    
    printf("Bool val: %d\n", is_valid); // Output: Bool val: 1
    return 0;
}
```

## 2. Modern Way (C23)
Identical zero-parity logic, using native Boolean keywords.

```c
#include <stdio.h> // Required for printf

int main() {
    auto x = 10;
    bool is_valid = (x != 0); // Native keyword
    
    if (x) { 
        printf("X is True\n"); // Output: X is True
    }
    
    if (0) { /* This never runs */ }
    
    printf("Bool val: %d\n", is_valid); // Output: Bool val: 1
    return 0;
}
```

# The Logic Bridge
// Logic: The CPU hardware flags (like the Zero Flag - ZF) are used by branch instructions (like `JZ` or `JNZ`) to determine truth based on whether a register contains zero.
