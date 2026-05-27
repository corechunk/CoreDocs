# 🔴 Standard: Storage Classes [SYSTEMS]

## Definition
Storage classes define the persistence and linkage of variables, telling the compiler whether to use the temporary Stack, permanent RAM, or high-speed Registers.

## 1. Legacy Way (C99 / C11 / C17)
Manual control via keywords like `static` (RAM) and `register` (CPU).

```c
#include <stdio.h>

void counter() {
    static int calls = 0; // Stays in RAM after function exits
    calls++;
    printf("Calls: %d\n", calls);
}

int main() {
    register int i = 0; // Hint to CPU to use a register for speed
    counter(); // Output: Calls: 1
    counter(); // Output: Calls: 2
    return 0;
}
```

## 2. Modern Way (C23)
Same rules, but adding `thread_local` for modern multi-threaded execution.

```c
#include <stdio.h>

// thread_local: Unique copy for each thread (C11/C23 Native)
thread_local int thread_id = 1; 

int main() {
    // Note: 'register' is NOT used here.
    // Logic: Modern compilers (C23) are so efficient at register 
    // allocation that the 'register' keyword is now ignored/redundant.
    
    static int calls = 0; 
    calls++;
    printf("Calls: %d\n", calls); // Output: Calls: 1
    return 0;
}
```

# The Logic Bridge
// Logic: The `static` keyword moves a variable's address from the "Stack" (deleted on return) to the "Data Segment" (exists for the program's entire life).
