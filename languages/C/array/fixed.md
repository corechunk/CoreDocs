# 🔴 Standard: Fixed-Size Arrays [SYSTEMS]

## Definition
Fixed-size arrays have their dimensions determined at compile-time. This ensures the compiler can pre-calculate the exact stack space needed.

## 1. Legacy Way (C99 / C11 / C17)
Explicit size declaration using constants or literals.

```c
#include <stdio.h>

int main() {
    int arr[5] = {1, 2, 3, 4, 5};
    size_t size = sizeof(arr);
    
    printf("Bytes: %zu\n", size); // Output: Bytes: 20 (on 32-bit int systems)
    return 0;
}
```

## 2. Modern Way (C23)
Mirroring task using `constexpr` for cleaner, type-safe sizing.

```c
#include <stdio.h>

int main() {
    constexpr int LEN = 5;
    int arr[LEN] = {1, 2, 3, 4, 5};
    
    size_t size = sizeof(arr);
    printf("Bytes: %zu\n", size); // Output: Bytes: 20
    return 0;
}
```

# The Logic Bridge
// Logic: Fixed arrays live on the Stack. Their size is embedded in the binary's instruction set, so no runtime memory allocation is performed.
