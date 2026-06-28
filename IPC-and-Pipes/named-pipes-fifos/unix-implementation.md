# 🐧 UNIX Named Pipes (FIFOs) Implementation

In UNIX systems, named pipes are created in the filesystem using `mkfifo()` and accessed using standard file operations (`open`, `read`, `write`, `close`).

---

### 💻 UNIX FIFO Client-Server in C

#### Server Program (Reads from FIFO)

```c
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <fcntl.h>
#include <sys/stat.h>

#define FIFO_PATH "/tmp/my_sys_fifo"

int main() {
    // Create FIFO node in filesystem
    unlink(FIFO_PATH);
    if (mkfifo(FIFO_PATH, 0666) == -1) {
        perror("mkfifo failed");
        return 1;
    }

    printf("Server: Waiting for client to connect...\n");
    // Blocks here until a client opens the FIFO for writing
    int fd = open(FIFO_PATH, O_RDONLY);
    if (fd == -1) return 1;
    printf("Server: Client connected.\n");

    char buffer[128];
    ssize_t bytes_read;
    while ((bytes_read = read(fd, buffer, sizeof(buffer) - 1)) > 0) {
        buffer[bytes_read] = '\0';
        printf("Received: %s", buffer);
    }

    close(fd);
    unlink(FIFO_PATH);
    return 0;
}
```

#### Client Program (Writes to FIFO)

```c
#include <stdio.h>
#include <fcntl.h>
#include <unistd.h>

#define FIFO_PATH "/tmp/my_sys_fifo"

int main() {
    printf("Client: Connecting to server...\n");
    // Blocks here until the server opens the FIFO for reading
    int fd = open(FIFO_PATH, O_WRONLY);
    if (fd == -1) {
        perror("Failed to connect to server FIFO");
        return 1;
    }

    printf("Client: Connected. Sending data...\n");
    write(fd, "Hello from the POSIX FIFO client!\n", 34);

    close(fd);
    return 0;
}
```
