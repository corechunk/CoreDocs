# 🟢 Standard: Conditionals [CORE]

## Definition
Conditionals control the flow of execution based on boolean logic. This hub covers the two primary branching mechanisms in C.

## 1. Legacy Way (C99 / C11 / C17)
Branching using standard `if` and `switch`.

```c
#include <stdio.h>

int main() {
    int code = 1;
    
    // If/Else Path
    if (code == 1) {
        printf("Active\n"); // Output: Active
    } else {
        printf("Idle\n");
    }
    
    // Switch Path
    switch (code) {
        case 1: printf("One\n"); break; // Output: One
        default: printf("Other\n");
    }
    return 0;
}
```

## 2. Modern Way (C23)
Identical branching logic, mirrored task.

```c
#include <stdio.h> // Required for printf

int main() {
    auto code = 1;
    
    // If/Else Path
    if (code == 1) {
        printf("Active\n"); // Output: Active
    } else {
        printf("Idle\n");
    }
    
    // Switch Path
    switch (code) {
        case 1: printf("One\n"); break; // Output: One
        default: printf("Other\n");
    }
    return 0;
}
```

## Deep-Dive Reference
For nested logic and fall-through behavior:
- [if-else.md](./control/if-else.md) | [switch.md](./control/switch.md)

# The Logic Bridge
// Logic: An `if-else` is a sequence of conditional jumps, while a `switch` is often optimized by the compiler into a "Jump Table," making it faster for a large number of constant cases.
