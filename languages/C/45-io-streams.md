# 🟢 Standard: I/O Streams [CORE]

## Definition
C provides three standard streams for program interaction: `stdin` (input), `stdout` (standard output), and `stderr` (error output). This mirror shows how these streams are accessed and differentiated.

## 1. Legacy Way (C99 / C11 / C17)
Using `fprintf` and `stdout`/`stderr` macros.

```c
#include <stdio.h>

int main() {
    // Normal Output
    fprintf(stdout, "Status: OK\n"); // Output: Status: OK
    
    // Error Output (Usually not buffered)
    fprintf(stderr, "Error: Fail\n"); // Output: Error: Fail
    
    return 0;
}
```

## 2. Modern Way (C23)
Identical stream logic, mirroring the task while using `auto`.

```c
#include <stdio.h> // Required for printf

int main() {
    // Mirror same task
    fprintf(stdout, "Status: OK\n");
    fprintf(stderr, "Error: Fail\n");
    
    return 0;
}
```

# The Logic Bridge
// Logic: Standard streams are file descriptors (0, 1, 2) that the Kernel provides to every process. `stdout` is usually line-buffered, while `stderr` is unbuffered so errors appear instantly even if the program crashes.
