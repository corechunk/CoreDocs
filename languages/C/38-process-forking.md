# 🔴 Standard: Process Forking [SYSTEMS]

## Definition
Process management in C (on POSIX systems) uses `fork()` to clone the current process and `exec()` to replace the process with a new program. This hub covers the foundations of multi-process execution.

## 1. Legacy Way (C99 / C11 / C17)
Standard POSIX process creation using `fork`.

```c
#include <stdio.h>
#include <unistd.h>
#include <sys/wait.h>

int main() {
    pid_t pid = fork();

    if (pid == 0) {
        // Child Process
        printf("Child Process\n"); // Output: Child Process
    } else if (pid > 0) {
        // Parent Process
        wait(NULL); // Wait for child
        printf("Child Finished\n"); // Output: Child Finished
    }
    return 0;
}
```

## 2. Modern Way (C23)
Identical POSIX mechanism, mirroring the same task with `auto` for process IDs.

```c
#include <stdio.h>
#include <unistd.h>
#include <sys/wait.h>

int main() {
    // auto: Native keyword for cleaner PID handling
    auto pid = fork();

    if (pid == 0) {
        printf("Child Process\n"); // Output: Child Process
    } else if (pid > 0) {
        wait(nullptr); // C23 nullptr
        printf("Child Finished\n"); // Output: Child Finished
    }
    return 0;
}
```

## Deep-Dive Reference
For process cloning and program replacement details:
- [fork.md](./concurrency/fork.md) | [exec.md](./concurrency/exec.md)

# The Logic Bridge
// Logic: `fork()` creates a nearly identical copy of the calling process by duplicating the Page Tables. Both processes continue execution from the point of the `fork()` call, distinguishing themselves only by the return value of the function.
