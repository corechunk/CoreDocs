# 🔴 Standard: Special Purpose Types [SYSTEMS]

## Definition
Types used for memory addresses (`void*`), object sizes (`size_t`), and "nothingness" (`nullptr`).

## 1. Legacy Way (C99 / C11 / C17)
Requires `stddef.h` or `stdio.h` for the `NULL` macro.

```c
#include <stdio.h> 
#include <stddef.h> // REQUIRED for NULL (Same for C11/C17)

int main() {
    void* ptr = NULL; // Macro: defined as (void*)0
    size_t size = sizeof(int);

    if (ptr == NULL) {
        printf("Empty, size: %zu\n", size); // Output: Empty, size: 4
    }
    return 0;
}
```

## 2. Modern Way (C23)
`nullptr` and `auto` are now native keywords.

```c
#include <stdio.h> // Required for printf

int main() {
    // nullptr/auto: Native keywords. No header.
    void* ptr = nullptr; 
    auto size = sizeof(int); 

    if (ptr == nullptr) {
        printf("Empty, size: %zu\n", size); // Output: Empty, size: 4
    }
    return 0;
}
```

# The Logic Bridge
// Logic: `size_t` is an unsigned integer that automatically scales to the system's word size (4 bytes on 32-bit, 8 bytes on 64-bit) to represent the largest possible memory object.
