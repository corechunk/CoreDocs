# 🟢 Standard: Logical Operators [CORE]

## Definition
Operators used to evaluate Boolean logic: `&&` (AND), `||` (OR), and `!` (NOT).

## 1. Legacy Way (C99 / C11 / C17)
Requires `stdbool.h`.

```c
#include <stdio.h>
#include <stdbool.h> // REQUIRED

int main() {
    bool x = true, y = false;
    
    printf("AND: %d\n", x && y); // Output: AND: 0
    printf("OR:  %d\n", x || y); // Output: OR: 1
    printf("NOT: %d\n", !x);     // Output: NOT: 0
    return 0;
}
```

## 2. Modern Way (C23)
Native Boolean keywords, no header.

```c
#include <stdio.h> // Required for printf

int main() {
    bool x = true, y = false; // Native
    
    printf("AND: %d\n", x && y); // Output: AND: 0
    printf("OR:  %d\n", x || y); // Output: OR: 1
    printf("NOT: %d\n", !x);     // Output: NOT: 0
    return 0;
}
```

# The Logic Bridge
// Logic: C uses "Short-circuit evaluation." For an `&&`, if the first part is false, the second part is never even looked at by the CPU, saving execution time.
