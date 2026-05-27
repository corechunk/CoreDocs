# 🔴 Standard: Stack vs. Heap [SYSTEMS]

## Definition
The two primary memory regions. **Stack** is automatic and fast (local variables); **Heap** is manual and large (persistent data).

## 1. Legacy Way (C99 / C11 / C17)
Showing stack vs heap storage.

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int stack_var = 10; // Stack (Automatic)
    int* heap_var = malloc(sizeof(int)); // Heap (Manual)

    printf("Stack: %p\n", (void*)&stack_var);
    printf("Heap:  %p\n", (void*)heap_var);
    
    free(heap_var);
    return 0;
}
```

## 2. Modern Way (C23)
Mirroring task with `auto` and `nullptr`.

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    auto stack_var = 10;
    auto heap_var = (int*)malloc(sizeof(int));

    if (heap_var != nullptr) {
        printf("Stack: %p\n", (void*)&stack_var);
        printf("Heap:  %p\n", (void*)heap_var);
        free(heap_var);
    }
    return 0;
}
```

# The Logic Bridge
// Logic: The Stack grows and shrinks automatically with function calls. The Heap is a pool of memory managed by the Kernel, requiring explicit pointers to access.
