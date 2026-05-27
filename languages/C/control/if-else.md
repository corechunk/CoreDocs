# 🟢 Standard: If/Else Logic [CORE]

## Definition
The primary decision-making structure in C.

## 1. Legacy Way (C99 / C11 / C17)
Standard branching.

```c
#include <stdio.h>

int main() {
    int score = 85;
    
    if (score >= 90) {
        printf("A\n");
    } else if (score >= 80) {
        printf("B\n"); // Output: B
    } else {
        printf("F\n");
    }
    return 0;
}
```

## 2. Modern Way (C23)
Mirroring task using `auto`.

```c
#include <stdio.h>

int main() {
    auto score = 85;
    
    if (score >= 90) {
        printf("A\n");
    } else if (score >= 80) {
        printf("B\n"); // Output: B
    } else {
        printf("F\n");
    }
    return 0;
}
```

# The Logic Bridge
// Logic: If/Else chains are evaluated sequentially. As soon as one condition is True, the rest are skipped by the CPU.
