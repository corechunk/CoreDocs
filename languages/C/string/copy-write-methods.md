# 🔵 Standard: String Copy & Write Methods [PRO]

## Definition
String Copy and Write Methods manage duplicating and formatting strings. Modern standards rank these operations based on their capability to guarantee null-termination and bounds constraints.

## 1. Legacy Way (C99)
Legacy copying relies on raw memory transfers (`strcpy`) that copy characters sequentially until they reach a null byte (`\0`), ignoring buffer size constraints.

```c
#include <stdio.h>
#include <string.h>

int main() {
    char dest[6];
    char *src = "TooLong";
    
    // UNSAFE: strcpy does not know dest limits, causing memory corruption
    // strcpy(dest, src);
    return 0;
}
```

## 2. Modern Way (C23 / C11)
Modern routines enforce target bounds verification (`snprintf`) and dynamic replication (`strdup`) with explicit resource lifecycle cleanup.

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main() {
    char dest[6];
    char *src = "SuperLong";

    // 1. Safe snprintf (Highly recommended copy alternative)
    snprintf(dest, sizeof(dest), "%s", src); // dest becomes "Super\0"
    printf("snprintf copy: %s\n", dest);

    // 2. Safe Heap replication
    char *heap_copy = strdup("Dynamic"); // Allocates heap and copies string
    if (heap_copy != NULL) {
        printf("Heap copy: %s\n", heap_copy);
        free(heap_copy);
    }
    return 0;
}
```

## Deep-Dive Reference
### The Copy & Write Security Rankings

1. **`snprintf(dest, size, "%s", src)` (Rank: 1 - Gold Standard / Safest)**
   - *Behavior*: Formats input directly into the destination buffer up to `size - 1` bytes.
   - *Null-Termination*: Always guarantees null-termination (`\0`).
2. **`strdup(src)` (Rank: 2 - Safe / Dynamic Allocation)**
   - *Behavior*: Calculates string length dynamically, allocates matching heap memory using `malloc`, and copies the string.
   - *Gotcha*: Must release memory using `free` when finished to prevent leaks.
3. **`strncpy(dest, src, size)` (Rank: 3 - Legacy Bounded / High Risk)**
   - *Behavior*: Copies up to `size` characters into `dest`.
   - *Gotcha*: If `strlen(src) >= size`, **no null terminator** is appended to `dest`. You must force truncation manually:
     ```c
     strncpy(dest, src, sizeof(dest) - 1);
     dest[sizeof(dest) - 1] = '\0';
     ```
4. **`strcpy(dest, src)` (Rank: 4 - Unsafe / Deprecated)**
   - *Behavior*: Blindly copies bytes to `dest` until a null terminator is reached in `src`. Exposes the program to buffer overflows.

# The Logic Bridge
// Logic: `strcpy` uses a simple loop copying bytes until it encounters zero. If the source string lacks a null terminator or the destination is too small, it continues writing bytes sequentially, overriding adjacent active stack frame regions.
