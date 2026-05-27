# 🟢 Standard: Switch Case [CORE]

## Definition
A specialized multi-way branch that matches an integer or character against constant values.

## 1. Legacy Way (C99 / C11 / C17)
Requires `break` to prevent fall-through.

```c
#include <stdio.h>

int main() {
    char grade = 'B';
    
    switch (grade) {
        case 'A': printf("Great\n"); break;
        case 'B': printf("Good\n");  break; // Output: Good
        default:  printf("Invalid\n");
    }
    return 0;
}
```

## 2. Modern Way (C23)
Mirroring task. C23 adds the `[[fallthrough]]` attribute to make intentional fall-through explicit.

```c
#include <stdio.h>

int main() {
    char grade = 'B';
    
    switch (grade) {
        case 'A': printf("Great\n"); break;
        case 'B': printf("Good\n");  break; // Output: Good
        default:  printf("Invalid\n");
    }
    return 0;
}
```

# The Logic Bridge
// Logic: Switches are optimized into a "Jump Table"—an array of addresses where the CPU can jump directly to the correct case in O(1) time.
