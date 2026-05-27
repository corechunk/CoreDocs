# 🔵 Standard: Redirection & Piping [PRO]

## Definition
Redirection and piping allow a C program to manipulate its own input/output streams, effectively connecting to other files or processes using `dup2()` and `pipe()`.

## 1. Legacy Way (C99 / C11 / C17)
Standard POSIX `pipe` initialization.

```c
#include <stdio.h>
#include <unistd.h>

int main() {
    int pipe_fds[2];
    
    // Create pipe
    if (pipe(pipe_fds) != -1) {
        printf("Pipe Created\n"); // Output: Pipe Created
        close(pipe_fds[0]);
        close(pipe_fds[1]);
    }
    return 0;
}
```

## 2. Modern Way (C23)
Mirroring the pipe creation task using `auto`.

```c
#include <stdio.h>
#include <unistd.h>

int main() {
    int pipe_fds[2];
    
    // Mirror same task
    auto result = pipe(pipe_fds);

    if (result != -1) {
        printf("Pipe Created\n"); // Output: Pipe Created
        close(pipe_fds[0]);
        close(pipe_fds[1]);
    }
    return 0;
}
```

# The Logic Bridge
// Logic: A pipe creates a unidirectional data channel in the Kernel's memory. `dup2()` is then used to overwrite the process's `stdout` or `stdin` with one end of that pipe.
