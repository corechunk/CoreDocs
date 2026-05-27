# 🔴 Standard: Socket Basics [SYSTEMS]

## Definition
Networking in C++ relies on the BSD Sockets API (standard on POSIX) or libraries like **Boost.Asio** for high-level asynchronous I/O.

## 1. Legacy Way (C++11 / C++17)
Standard POSIX socket creation.

```cpp
#include <iostream>
#include <sys/socket.h>
#include <netinet/in.h>

int main() {
    int sock = socket(AF_INET, SOCK_STREAM, 0);
    if (sock != -1) {
        std::cout << "Socket Created\n"; // Output: Socket Created
    }
    return 0;
}
```

## 2. Modern Way (C23)
Mirroring task with `auto` and modern attributes.

```cpp
#include <iostream>
#include <sys/socket.h>
#include <netinet/in.h>

int main() {
    auto sock = socket(AF_INET, SOCK_STREAM, 0);
    if (sock != -1) {
        std::cout << "Socket Created\n"; // Output: Socket Created
    }
    return 0;
}
```

## Deep-Dive Reference
For network server/client rituals:
- [Listening](./network/listen.md) | [Connecting](./network/connect.md)

# The Logic Bridge
// Logic: A socket is a File Descriptor that the Kernel maps to a network protocol stack. Modern C++ focus is on abstracting these raw descriptors into type-safe stream objects.
