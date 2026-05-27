# 🟢 Standard: Assignment Operators [CORE]

## Definition
Operators used to store values in variables, including compound assignments like `+=`.

## 1. Legacy Way (C99 / C11 / C17)
Standard and compound assignments.

```c
#include <stdio.h>

int main() {
    int x = 10;
    x += 5; // Same as x = x + 5
    
    printf("X: %d\n", x); // Output: X: 15
    return 0;
}
```

## 2. Modern Way (C23)
Identical syntax, mirrored task.

```c
#include <stdio.h> // Required for printf

int main() {
    auto x = 10;
    x += 5; 
    
    printf("X: %d\n", x); // Output: X: 15
    return 0;
}
```

# The Logic Bridge
// Logic: Compound assignment (`+=`) is often a single CPU instruction (e.g., `ADD [mem], val`), making it slightly more efficient than reading, adding, and storing separately.
