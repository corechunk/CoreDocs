# ⚠️ Process Traps & Signals

Processes must monitor and clean up child states to prevent system resource leakage (zombies) and respond to asynchronous kernel interruptions (signals).

---

### 🧠 Zombie & Orphan Processes

*   **Zombie Process**: A terminated child process whose parent has not yet read its exit status via `wait()` / `waitpid()`. Its entry in the process table remains.
*   **Orphan Process**: A parent process terminates before its child. The child is re-parented to `init` (PID 1), which automatically reaps it upon termination.

---

### 💻 POSIX C: Non-Blocking Reaping & Signal Handling

```c
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <sys/wait.h>
#include <signal.h>

// Signal handler to asynchronously catch SIGCHLD (sent when child terminates)
void handle_sigchld(int sig) {
    (void)sig;
    // Reap all terminated child processes without blocking the parent thread
    while (waitpid(-1, NULL, WNOHANG) > 0);
}

int main() {
    // Register the SIGCHLD signal handler
    struct sigaction sa;
    sa.sa_handler = handle_sigchld;
    sigemptyset(&sa.sa_mask);
    sa.sa_flags = SA_RESTART | SA_NOCLDSTOP;
    sigaction(SIGCHLD, &sa, NULL);

    pid_t pid = fork();
    if (pid == 0) {
        printf("Child (PID %d) running for 1s...\n", getpid());
        sleep(1);
        printf("Child exiting.\n");
        exit(0);
    }

    // Parent continues its normal event loop
    while (1) {
        printf("Parent executing main loop...\n");
        sleep(2);
    }
    return 0;
}
```
