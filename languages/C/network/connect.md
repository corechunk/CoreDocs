# 🔴 Standard: Client Connection [SYSTEMS]

## Definition
The "Connect" ritual is the client-side process of requesting a connection to a specific Server IP and Port.

## 1. Legacy Way (C99 / C11 / C17)
Standard connection request using `sockaddr_in`.

```c
#include <stdio.h>
#include <sys/socket.h>
#include <arpa/inet.h>

int main() {
    int sock = socket(AF_INET, SOCK_STREAM, 0);
    printf("Connecting to 127.0.0.1...\n"); // Output: Connecting to 127.0.0.1...
    
    return 0;
}
```

## 2. Modern Way (C23)
Mirroring same task.

```c
#include <stdio.h>
#include <sys/socket.h>
#include <arpa/inet.h>

int main() {
    auto sock = socket(AF_INET, SOCK_STREAM, 0);
    printf("Connecting to 127.0.0.1...\n"); // Output: Connecting to 127.0.0.1...
    
    return 0;
}
```

# The Logic Bridge
// Logic: `connect` initiates the TCP handshake. The process blocks (stops) until the server acknowledges the request or a timeout occurs.
