# 🟢 Standard: Indefinite Iteration [CORE]

## Definition
Indefinite loops (`while` and `do-while`) continue as long as a condition remains True. `while` checks at the start, `do-while` checks at the end (guaranteeing at least one execution).

## 1. Legacy Way (C99 / C11 / C17)
Requires `stdbool.h` for native boolean conditions.

```c
#include <stdio.h>
#include <stdbool.h> // REQUIRED

int main() {
    int i = 0;
    bool running = true;
    
    while (running) {
        printf("Step %d\n", i); // Output: Step 0
        i++;
        if (i == 1) running = false;
    }
    
    do {
        printf("Final\n"); // Output: Final
    } while (0); // False, stops after 1st run
    
    return 0;
}
```

## 2. Modern Way (C23)
Identical logic, using native Boolean keywords.

```c
#include <stdio.h> // Required for printf

int main() {
    auto i = 0;
    bool running = true; // Native
    
    while (running) {
        printf("Step %d\n", i); // Output: Step 0
        i++;
        if (i == 1) running = false;
    }
    
    do {
        printf("Final\n"); // Output: Final
    } while (0);
    
    return 0;
}
```

# The Logic Bridge
// Logic: Indefinite loops rely on conditional jump instructions (`JMP`). `while` is a "Top-tested" loop, while `do-while` is "Bottom-tested."
