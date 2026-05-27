# 🔴 Standard: Process Cloning (fork) [SYSTEMS]

## Definition
`fork()` creates a new process (the child) by making an exact copy of the calling process (the parent).

## 1. Legacy Way (C99 / C11 / C17)
Standard usage with `pid_t`.

```c
#include <stdio.h>
#include <unistd.h>

int main() {
    pid_t pid = fork();
    
    if (pid == 0) {
        printf("I am child\n"); // Output: I am child
    } else {
        printf("I am parent\n"); // Output: I am parent
    }
    return 0;
}
```

## 2. Modern Way (C23)
Mirroring the same task using `auto`.

```c
#include <stdio.h>
#include <unistd.h>

int main() {
    auto pid = fork();
    
    if (pid == 0) {
        printf("I am child\n"); // Output: I am child
    } else {
        printf("I am parent\n"); // Output: I am parent
    }
    return 0;
}
```

# The Logic Bridge
// Logic: After `fork()`, two independent processes exist, each with its own memory space, but starting with identical data.
