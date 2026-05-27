# 🔴 Standard: Program Replacement (exec) [SYSTEMS]

## Definition
The `exec` family of functions replaces the current process image with a new process image (a different program).

## 1. Legacy Way (C99 / C11 / C17)
Using `execl` to run the `ls` command.

```c
#include <stdio.h>
#include <unistd.h>

int main() {
    printf("Running ls...\n"); // Output: Running ls...
    execl("/bin/ls", "ls", "-l", NULL);
    
    // This part only runs if exec fails
    return 1;
}
```

## 2. Modern Way (C23)
Mirroring the same task using `nullptr`.

```c
#include <stdio.h>
#include <unistd.h>

int main() {
    printf("Running ls...\n"); // Output: Running ls...
    // C23 nullptr instead of NULL
    execl("/bin/ls", "ls", "-l", nullptr);
    
    return 1;
}
```

# The Logic Bridge
// Logic: `exec` does not create a new process; it transforms the current process into a new one. The original code after a successful `exec` call is never executed.
