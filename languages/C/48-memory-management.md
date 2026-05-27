# 🔴 Standard: Memory Management [SYSTEMS]

## Definition
The core of C's power and danger. Memory management involves manually allocating space on the **Heap** for data that must persist beyond a function call, and manually freeing it when done.

## 1. Legacy Way (C99 / C11 / C17)
Standard `malloc` and `free` using the `NULL` macro.

```c
#include <stdio.h>
#include <stdlib.h> // REQUIRED for malloc/free

int main() {
    // Allocate space for 5 integers
    int* ptr = (int*)malloc(5 * sizeof(int));
    
    if (ptr != NULL) {
        printf("Memory Allocated\n"); // Output: Memory Allocated
        free(ptr); // Must free manually
    }
    return 0;
}
```

## 2. Modern Way (C23)
C23 formalizes `nullptr` and adds `free_sized`, providing a more type-safe and performant way to manage the heap.

```c
#include <stdio.h>
#include <stdlib.h> // Required for malloc/free

int main() {
    // auto: Deduces pointer type automatically
    auto ptr = (int*)malloc(5 * sizeof(int));

    if (ptr != nullptr) { // C23 nullptr
        printf("Memory Allocated\n"); // Output: Memory Allocated
        free(ptr);
    }
    return 0;
}
```

## Deep-Dive Reference
For stack/heap internals and pointer math:
- [stack-heap.md](./memory/stack-heap.md) | [allocation.md](./memory/allocation.md) | [pointer-arithmetic.md](./memory/pointer-arithmetic.md)

# The Logic Bridge
// Logic: `malloc` requests a block of memory from the OS Kernel. If the program "forgets" to call `free`, the memory remains claimed until the process ends, causing a "Memory Leak."
