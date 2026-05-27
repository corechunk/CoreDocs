# Static & Linkage (PRO)

Definition: Linkage determines how symbols (functions/variables) are visible across different files (translation units). C uses `static` for internal linkage and `extern` for external linkage.

## 1. Legacy Way (C99 / C11 / C17)
Standard usage of `static` to hide functions.

```c
// In file: helpers.c
static void internal_task() { 
    // Only visible in this file
}

void public_task() {
    internal_task();
}
```

## 2. Modern Way (C23)
Using `static` with C23's better attribute handling and `thread_local` (C11/C23).

```c
#include <stdio.h>

static thread_local int counter = 0; // File-local and thread-safe

static void log_info(const char* msg) {
    printf("[LOG]: %s\n", msg);
}

int main() {
    log_info("Static linkage");
    return 0;
}
```

# The Logic Bridge
// Logic: `static` on a global symbol changes its linkage from **External** (visible to the linker) to **Internal** (private to the object file). This reduces binary size by preventing the linker from exporting the symbol and prevents name collisions between different files.
