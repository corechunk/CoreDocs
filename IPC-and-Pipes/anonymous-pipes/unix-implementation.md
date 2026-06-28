# 🐧 UNIX Anonymous Pipes Implementation

In POSIX systems, anonymous pipes are allocated using the `pipe()` system call and redirected using `dup2()`.

---

### 🧠 The File Descriptor Table & Redirection

When a parent process spawns a child, the child inherits a copy of the parent's File Descriptor (FD) table. By duplicating the pipe FDs into standard input (0) or standard output (1) via `dup2()`, we redirect the streams of child programs (such as running `ls | grep`).

```text
Parent FD Table                       Child FD Table (After dup2)
+-------------+                       +-------------------------+
| 0: stdin    |                       | 0: stdin                |
| 1: stdout   |                       | 1: pipe_write (clone)   | <--- Replaces stdout
| 2: stderr   |                       | 2: stderr               |
| 3: pipe_read|                       | 3: pipe_read            |
| 4: pipe_writ|                       | 4: pipe_write           |
+-------------+                       +-------------------------+
```

---

### 💻 UNIX Pipeline Implementation in C

The following complete program implements the logical equivalent of the shell command: `ls -l | grep .txt`

```c
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <sys/types.h>
#include <sys/wait.h>

int main() {
    int pipefds[2]; // pipefds[0] = read, pipefds[1] = write

    if (pipe(pipefds) == -1) {
        perror("pipe failed");
        return 1;
    }

    pid_t pid1 = fork();
    if (pid1 == 0) {
        // Child 1 (Writer): Runs "ls -l"
        // Redirect stdout (1) to the write-end of the pipe
        dup2(pipefds[1], STDOUT_FILENO);
        
        // Close duplicate descriptors to prevent resources staying open
        close(pipefds[0]);
        close(pipefds[1]);

        char *args[] = {"/usr/bin/ls", "-l", NULL};
        execve(args[0], args, NULL);
        perror("execve ls failed");
        exit(1);
    }

    pid_t pid2 = fork();
    if (pid2 == 0) {
        // Child 2 (Reader): Runs "grep .txt"
        // Redirect stdin (0) to the read-end of the pipe
        dup2(pipefds[0], STDIN_FILENO);

        // Close unused pipe descriptors
        close(pipefds[0]);
        close(pipefds[1]);

        char *args[] = {"/usr/bin/grep", ".txt", NULL};
        execve(args[0], args, NULL);
        perror("execve grep failed");
        exit(1);
    }

    // Parent closes its references to the pipe so readers/writers see EOF/SIGPIPE correctly
    close(pipefds[0]);
    close(pipefds[1]);

    // Reap both child processes
    waitpid(pid1, NULL, 0);
    waitpid(pid2, NULL, 0);

    return 0;
}
```
