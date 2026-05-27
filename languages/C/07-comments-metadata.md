# 🟢 Standard: Comments & Metadata [CORE]

## Definition
Text ignored by the compiler, used to document intent for humans or provide instructions for external documentation tools.

## 1. Legacy Way (C99 / C11 / C17)
Standard single and multi-line comments for general notes.

```c
#include <stdio.h>

/* Global Configuration */
int main() {
    int x = 10; // Simple integer
    printf("X: %d\n", x); // Output: X: 10
    return 0;
}
```

## 2. Modern Way (C23)
Standardized Doxygen patterns parsed by documentation generators (like Doxygen).

```c
#include <stdio.h>

/**
 * @file main.c
 * @brief Simple Entry Point
 * @return integer status
 */
int main() {
    int x = 10;
    printf("X: %d\n", x); // Output: X: 10
    return 0;
}
```

# The Logic Bridge
// Logic: The Preprocessor physically deletes comments before the Compiler stage, so they have zero impact on final program speed or size.
