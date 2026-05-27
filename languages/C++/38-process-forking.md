# 🔴 Standard: Process Management [SYSTEMS]

## Definition
C++ process management relies on the OS API. `fork()` clones the current process, and `exec()` replaces it. Modern C++ focus is more on Threads, but Process logic is vital for systems engineering.

## 1. Legacy Way (C++11 / C++17)
Standard POSIX `fork`.

```cpp
#include <iostream>
#include <unistd.h>
#include <sys/wait.h>

int main() {
    pid_t pid = fork();
    if (pid == 0) {
        std::cout << "Child\n"; // Output: Child
    } else {
        wait(NULL);
        std::cout << "Parent\n"; // Output: Parent
    }
    return 0;
}
```

## 2. Modern Way (C23)
Mirroring task using `auto`.

```cpp
#include <iostream>
#include <unistd.h>
#include <sys/wait.h>

int main() {
    auto pid = fork();
    if (pid == 0) {
        std::cout << "Child\n"; // Output: Child
    } else {
        wait(nullptr);
        std::cout << "Parent\n"; // Output: Parent
    }
    return 0;
}
```

## Deep-Dive Reference
For process spawning and replacement:
- [Forking](./concurrency/fork.md) | [Execution](./concurrency/exec.md)

# The Logic Bridge
// Logic: `fork()` uses Copy-on-Write (CoW). The Kernel doesn't physically copy memory until one of the processes tries to write to it, making cloning extremely efficient.
