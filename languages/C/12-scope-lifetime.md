# 🟢 Standard: Scope & Lifetime [CORE]

## Definition
Scope is visibility (where the name works). Lifetime is storage (how long the memory exists). Curly braces `{}` are the primary masters of both in C.

## 1. Legacy Way (C99 / C11 / C17)
Variables are localized to the block where they are declared.

```c
#include <stdio.h>

int main() {
    int x = 5; // Scope: Entire main()
    
    for (int i = 0; i < 2; i++) {
        int y = 10; // Scope: Only this loop
        printf("Loop %d: %d\n", i, y); 
        // Output (Iteration 0): Loop 0: 10
        // Output (Iteration 1): Loop 1: 10
    }
    // i and y are no longer visible here
    
    printf("X: %d\n", x); // Output: X: 5
    return 0;
}
```

## 2. Modern Way (C23)
Scope rules remain identical, but `auto` provides cleaner block-level declarations.

```c
#include <stdio.h> // Required for printf

int main() {
    auto x = 5; // Scope: Entire main()
    
    for (auto i = 0; i < 2; i++) {
        auto y = 10; // Scope: Only this loop
        printf("Loop %d: %d\n", i, y);
        // Output (Iteration 0): Loop 0: 10
        // Output (Iteration 1): Loop 1: 10
    }
    
    printf("X: %d\n", x); // Output: X: 5
    return 0;
}
```

# The Logic Bridge
// Logic: Local variables are stored on the "Stack"; exiting a block simply moves the stack pointer back, reclaiming that memory for the next operation.
