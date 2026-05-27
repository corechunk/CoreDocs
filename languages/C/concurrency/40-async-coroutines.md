# 🔵 Standard: Async & Coroutines [PRO]

## Definition
Standard C does not have built-in `async/await` or native coroutines. Asynchronous behavior is achieved via **Non-blocking I/O** using systems calls like `poll()` or `select()`, allowing a program to monitor multiple streams without stopping.

## 1. Legacy Way (C99 / C11 / C17)
Monitoring `stdin` with `poll` and standard macros.

```c
#include <stdio.h>
#include <poll.h>

int main() {
    struct pollfd fds[1];
    fds[0].fd = 0; // STDIN
    fds[0].events = POLLIN;

    // Wait 100ms for input
    int ret = poll(fds, 1, 100);
    
    if (ret == 0) {
        printf("Timeout\n"); // Output: Timeout
    }
    return 0;
}
```

## 2. Modern Way (C23)
Mirroring the same monitoring task with `nullptr` and C23 improvements.

```c
#include <stdio.h>
#include <poll.h>

int main() {
    struct pollfd fds[1] = {
        { .fd = 0, .events = POLLIN } // Designated initializer
    };

    // Mirror same task
    auto ret = poll(fds, 1, 100);
    
    if (ret == 0) {
        printf("Timeout\n"); // Output: Timeout
    }
    return 0;
}
```

# The Logic Bridge
// Logic: `poll` is a Kernel-level operation that puts the process to sleep until an event occurs on a file descriptor, preventing the CPU from wasting cycles in a "busy-wait" loop.
