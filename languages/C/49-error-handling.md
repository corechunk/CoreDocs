# 🟢 Standard: Error Handling [CORE]

## Definition
C uses **Return Codes** and the global `errno` variable to signal errors. Unlike higher languages, C has no built-in `try/catch`.

## 1. Legacy Way (C99 / C11 / C17)
Checking `errno` after a system call.

```c
#include <stdio.h>
#include <errno.h>
#include <string.h>

int main() {
    FILE* f = fopen("nonexistent.txt", "r");
    
    if (f == NULL) {
        printf("Error: %s\n", strerror(errno)); 
        // Output: Error: No such file or directory
    }
    return 0;
}
```

## 2. Modern Way (C23)
Mirroring the error check with `nullptr` and `auto`.

```c
#include <stdio.h>
#include <errno.h>
#include <string.h>

int main() {
    // Mirror same task
    auto f = fopen("nonexistent.txt", "r");
    
    if (f == nullptr) {
        printf("Error: %s\n", strerror(errno)); 
        // Output: Error: No such file or directory
    }
    return 0;
}
```

# The Logic Bridge
// Logic: `errno` is a thread-local integer. Most library functions return a sentinel value (like -1 or NULL) to tell you "Look at errno for the reason why I failed."
