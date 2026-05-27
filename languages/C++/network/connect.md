# 🔴 Standard: Client Connecting [SYSTEMS]

## Definition
Initiating a connection to a server.

## 1. Legacy Way (C++11 / C++17)
```cpp
#include <iostream>
#include <sys/socket.h>

int main() {
    int fd = socket(AF_INET, SOCK_STREAM, 0);
    std::cout << "Connecting to 127.0.0.1...\n"; // Output: Connecting to 127.0.0.1...
    return 0;
}
```

## 2. Modern Way (C23)
```cpp
#include <iostream>
#include <sys/socket.h>

int main() {
    auto fd = socket(AF_INET, SOCK_STREAM, 0);
    std::cout << "Connecting to 127.0.0.1...\n"; // Output: Connecting to 127.0.0.1...
    return 0;
}
```

# The Logic Bridge
// Logic: `connect` performs the transport-layer handshake (e.g., TCP SYN/ACK). It blocks the process until the connection is established or fails.
