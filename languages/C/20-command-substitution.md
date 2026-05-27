# 🔵 Standard: Command Substitution [PRO]

## Definition
Unlike Bash, C does not have native backticks or `$( )` syntax. Instead, it uses `popen()` to open a pipe to an external command's stream, effectively capturing its output into a C buffer.

## 1. Legacy Way (C99 / C11 / C17)
Standard POSIX `popen` workflow.

```c
#include <stdio.h>

int main() {
    char buffer[128];
    // Open process for reading ("r")
    FILE* pipe = popen("echo 'Legacy'", "r");
    
    if (pipe) {
        fgets(buffer, sizeof(buffer), pipe);
        printf("Out: %s", buffer); // Output: Out: Legacy
        pclose(pipe);
    }
    return 0;
}
```

## 2. Modern Way (C23)
Identical mechanism, as C23 continues to rely on POSIX for system-level execution.

```c
#include <stdio.h> // Required for printf/popen

int main() {
    char buffer[128];
    // Open process for reading
    FILE* pipe = popen("echo 'Modern'", "r");
    
    if (pipe) {
        fgets(buffer, sizeof(buffer), pipe);
        printf("Out: %s", buffer); // Output: Out: Modern
        pclose(pipe);
    }
    return 0;
}
```

# The Logic Bridge
// Logic: `popen` forks a shell, executes the command, and redirects the command's `stdout` to a file pointer that your C program can read like any other file.
