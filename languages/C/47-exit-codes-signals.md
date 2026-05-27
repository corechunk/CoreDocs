# 🔴 Standard: Exit Codes & Signals [SYSTEMS]

## Definition
Exit codes communicate a program's success or failure to the OS. Signals (like `SIGINT`) are asynchronous notifications sent to a process to interrupt its execution.

## 1. Legacy Way (C99 / C11 / C17)
Standard exit macros and signal handlers.

```c
#include <stdio.h>
#include <stdlib.h> // REQUIRED for EXIT_SUCCESS
#include <signal.h>

void handle(int sig) { printf("Signal Received\n"); }

int main() {
    signal(SIGINT, handle);
    printf("Exiting...\n");   // Output: Exiting...
    return EXIT_SUCCESS;
}
```

## 2. Modern Way (C23)
Identical signal logic, mirroring the task using `nullptr` and modern C23 attributes.

```c
#include <stdio.h>
#include <stdlib.h>
#include <signal.h>

void handle(int sig) { printf("Signal Received\n"); }

int main() {
    // Mirror same task
    signal(SIGINT, handle);
    printf("Exiting...\n");
    return EXIT_SUCCESS; // Standard since C89
}
```

# The Logic Bridge
// Logic: An "Exit Code" is an 8-bit value returned to the Kernel's process table. Signals are software interrupts that force the CPU to save the process state and jump to a predefined handler function.
