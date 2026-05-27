# 🟢 Standard: Definite Iteration (For) [CORE]

## Definition
The `for` loop is used for definite iteration, where the number of cycles is usually known beforehand. It consists of initialization, condition, and increment.

## 1. Legacy Way (C99 / C11 / C17)
Standard C loop with declaration inside the loop header (since C99).

```c
#include <stdio.h>

int main() {
    // Loop 3 times
    for (int i = 0; i < 3; i++) {
        printf("Count: %d\n", i);
    }
    // Output: Count: 0
    // Output: Count: 1
    // Output: Count: 2
    
    return 0;
}
```

## 2. Modern Way (C23)
Identical syntax, mirrored task using modern type inference for cleaner control variables.

```c
#include <stdio.h> // Required for printf

int main() {
    // Mirror: Loop 3 times using auto
    for (auto i = 0; i < 3; i++) {
        printf("Count: %d\n", i);
    }
    // Output: Count: 0
    // Output: Count: 1
    // Output: Count: 2

    return 0;
}
```

# The Logic Bridge
// Logic: A `for` loop is a syntactic wrapper around a `while` loop. The compiler sets up the counter, checks the condition, executes the body, and then jumps back to increment the counter.
