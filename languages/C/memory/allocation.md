# 🔴 Standard: Allocation Lifecycle [SYSTEMS]

## Definition
The four stages of heap memory: `malloc` (allocate), `calloc` (zero-allocate), `realloc` (resize), and `free` (release).

## 1. Legacy Way (C99 / C11 / C17)
Standard allocation ritual.

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int* arr = calloc(2, sizeof(int)); // Zeroed memory
    arr = realloc(arr, 4 * sizeof(int)); // Resized
    
    printf("Arr 0: %d\n", arr[0]); // Output: Arr 0: 0
    
    free(arr);
    return 0;
}
```

## 2. Modern Way (C23)
Mirroring same ritual with `nullptr`.

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    auto arr = (int*)calloc(2, sizeof(int));
    arr = (int*)realloc(arr, 4 * sizeof(int));
    
    if (arr != nullptr) {
        printf("Arr 0: %d\n", arr[0]); // Output: Arr 0: 0
        free(arr);
    }
    return 0;
}
```

# The Logic Bridge
// Logic: `realloc` may move the data to a completely new memory address if the current block doesn't have enough contiguous space to grow.
