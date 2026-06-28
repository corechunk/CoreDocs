# 🌐 UNIX Domain Sockets (UDS)

UNIX Domain Sockets (`AF_UNIX` / `AF_LOCAL`) provide high-performance local IPC by utilizing the standard POSIX sockets interface but bypassing the TCP/IP network protocol stack.

---

### 🧠 Performance & System Mechanics

*   **Network Bypass**: Because data routing is confined to a single kernel, UDS does not perform checksum calculations, header packaging, routing hops, or network interface buffering. Data is copied directly from the sender's memory to the receiver's socket buffer.
*   **Addressing**: Sockets are bound to standard filesystem nodes (e.g. `/tmp/local_ipc.sock`), allowing access control via UNIX file permissions.
*   **Socketpair Primitive**: `socketpair()` creates a connected, bidirectional socket channel directly without going through the address binding loop, ideal for parent-child IPC.

---

### 💻 UNIX Domain Socket (UDS) Server-Client in C

#### Server Program

```c
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <sys/socket.h>
#include <sys/un.h>

#define SOCK_PATH "/tmp/my_sys_socket.sock"

int main() {
    int server_fd = socket(AF_UNIX, SOCK_STREAM, 0);
    struct sockaddr_un addr;
    
    unlink(SOCK_PATH);
    memset(&addr, 0, sizeof(addr));
    addr.sun_family = AF_UNIX;
    strncpy(addr.sun_path, SOCK_PATH, sizeof(addr.sun_path) - 1);

    bind(server_fd, (struct sockaddr*)&addr, sizeof(addr));
    listen(server_fd, 5);

    printf("UDS Server: Waiting for client connection...\n");
    int client_fd = accept(server_fd, NULL, NULL);
    printf("UDS Server: Client connected.\n");

    char buffer[128];
    read(client_fd, buffer, sizeof(buffer) - 1);
    printf("Received: %s\n", buffer);

    close(client_fd);
    close(server_fd);
    unlink(SOCK_PATH);
    return 0;
}
```

#### Client Program

```c
#include <stdio.h>
#include <sys/socket.h>
#include <sys/un.h>
#include <unistd.h>

#define SOCK_PATH "/tmp/my_sys_socket.sock"

int main() {
    int client_fd = socket(AF_UNIX, SOCK_STREAM, 0);
    struct sockaddr_un addr;

    memset(&addr, 0, sizeof(addr));
    addr.sun_family = AF_UNIX;
    strncpy(addr.sun_path, SOCK_PATH, sizeof(addr.sun_path) - 1);

    if (connect(client_fd, (struct sockaddr*)&addr, sizeof(addr)) == -1) {
        perror("Connect failed");
        return 1;
    }

    write(client_fd, "Hello via AF_UNIX!", 18);
    close(client_fd);
    return 0;
}
```
