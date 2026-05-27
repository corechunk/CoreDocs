# 🔴 Standard: Socket Basics [SYSTEMS]

## Definition
Network communication in C (on POSIX systems) uses **Sockets**—software endpoints for sending and receiving data across a network. This hub covers the creation and fundamental ritual of connecting two processes.

## 1. Legacy Way (C99 / C11 / C17)
Standard socket initialization using the `NULL` macro and legacy type definitions.

```c
#include <stdio.h>
#include <sys/socket.h>
#include <netinet/in.h>

int main() {
    // Create TCP socket (IPv4)
    int sock = socket(AF_INET, SOCK_STREAM, 0);
    
    if (sock != -1) {
        printf("Socket Created\n"); // Output: Socket Created
    }
    
    // (Bind/Connect logic would follow)
    return 0;
}
```

## 2. Modern Way (C23)
Identical POSIX mechanism, mirroring the same task while using `auto` and `nullptr`.

```c
#include <stdio.h>
#include <sys/socket.h>
#include <netinet/in.h>

int main() {
    // auto: Native keyword for cleaner descriptor handling
    auto sock = socket(AF_INET, SOCK_STREAM, 0);

    if (sock != -1) {
        printf("Socket Created\n"); // Output: Socket Created
    }
    
    return 0;
}
```

## Deep-Dive Reference
For server-side listening and client-side connection rituals:
- [listen.md](./network/listen.md) | [connect.md](./network/connect.md)

# The Logic Bridge
// Logic: A socket is represented by a file descriptor (an integer). The Kernel treats network streams like files, allowing the same `read()` and `write()` calls to be used for both local files and global network connections.
