# 🔴 Standard: Server Listening [SYSTEMS]

## Definition
The "Listen" ritual is the server-side process of binding a socket to a port and waiting for incoming client connections.

## 1. Legacy Way (C99 / C11 / C17)
Standard bind/listen workflow.

```c
#include <stdio.h>
#include <sys/socket.h>
#include <netinet/in.h>

int main() {
    int server_fd = socket(AF_INET, SOCK_STREAM, 0);
    struct sockaddr_in address = { .sin_family = AF_INET, .sin_port = 8080 };

    // Bind and Listen
    printf("Listening on 8080...\n"); // Output: Listening on 8080...
    
    return 0;
}
```

## 2. Modern Way (C23)
Mirroring the same task.

```c
#include <stdio.h>
#include <sys/socket.h>
#include <netinet/in.h>

int main() {
    auto server_fd = socket(AF_INET, SOCK_STREAM, 0);
    struct sockaddr_in address = { .sin_family = AF_INET, .sin_port = 8080 };

    printf("Listening on 8080...\n"); // Output: Listening on 8080...
    
    return 0;
}
```

# The Logic Bridge
// Logic: `bind` assigns a name (IP/Port) to the socket, and `listen` tells the Kernel to queue up incoming connection requests.
