# 🔴 Standard: TCP vs. UDP Patterns [SYSTEMS]

## Definition
The two primary transport protocols. **TCP** (SOCK_STREAM) provides a reliable, ordered stream of bytes. **UDP** (SOCK_DGRAM) provides fast, "Fire-and-Forget" datagrams without a guaranteed delivery.

## 1. Legacy Way (C99 / C11 / C17)
Defining socket types using standard macros.

```c
#include <stdio.h>
#include <sys/socket.h>

int main() {
    // TCP: Connection-Oriented
    int tcp_sock = socket(AF_INET, SOCK_STREAM, 0);
    
    // UDP: Connectionless
    int udp_sock = socket(AF_INET, SOCK_DGRAM, 0);

    printf("TCP ID: %d\n", (tcp_sock != -1)); // Output: TCP ID: 1
    printf("UDP ID: %d\n", (udp_sock != -1)); // Output: UDP ID: 1
    return 0;
}
```

## 2. Modern Way (C23)
Mirroring the protocol task using `auto`.

```c
#include <stdio.h>
#include <sys/socket.h>

int main() {
    // Mirror same task
    auto tcp_sock = socket(AF_INET, SOCK_STREAM, 0);
    auto udp_sock = socket(AF_INET, SOCK_DGRAM, 0);

    printf("TCP ID: %d\n", (tcp_sock != -1)); // Output: TCP ID: 1
    printf("UDP ID: %d\n", (udp_sock != -1)); // Output: UDP ID: 1
    return 0;
}
```

# The Logic Bridge
// Logic: TCP performs a "Three-way handshake" to synchronize sequence numbers and ensure reliability, while UDP simply sends packets to an IP/Port without verifying if the receiver is ready.
