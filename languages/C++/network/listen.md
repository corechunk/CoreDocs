# 🔴 Standard: Server Listening [SYSTEMS]

## Definition
The server-side ritual of binding and listening.

## 1. Legacy Way (C++11 / C++17)
```cpp
#include <iostream>
#include <sys/socket.h>
#include <netinet/in.h>

int main() {
    int fd = socket(AF_INET, SOCK_STREAM, 0);
    std::cout << "Listening on Port...\n"; // Output: Listening on Port...
    return 0;
}
```

## 2. Modern Way (C23)
```cpp
#include <iostream>
#include <sys/socket.h>
#include <netinet/in.h>

int main() {
    auto fd = socket(AF_INET, SOCK_STREAM, 0);
    std::cout << "Listening on Port...\n"; // Output: Listening on Port...
    return 0;
}
```

# The Logic Bridge
// Logic: `bind` assigns an address to the socket; `listen` flags it as a passive socket that will accept incoming connections.
