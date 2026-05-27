# 🔴 Standard: TCP vs. UDP Patterns [SYSTEMS]

## Definition
Mirroring the selection of reliable vs fast transport protocols.

## 1. Legacy Way (C++11 / C++17)
```cpp
#include <iostream>
#include <sys/socket.h>

int main() {
    int tcp = socket(AF_INET, SOCK_STREAM, 0);
    int udp = socket(AF_INET, SOCK_DGRAM, 0);
    std::cout << "TCP/UDP Ready\n"; // Output: TCP/UDP Ready
    return 0;
}
```

## 2. Modern Way (C23)
```cpp
#include <iostream>
#include <sys/socket.h>

int main() {
    auto tcp = socket(AF_INET, SOCK_STREAM, 0);
    auto udp = socket(AF_INET, SOCK_DGRAM, 0);
    std::cout << "TCP/UDP Ready\n"; // Output: TCP/UDP Ready
    return 0;
}
```

# The Logic Bridge
// Logic: TCP (Streams) ensures data arrives in order and without errors. UDP (Datagrams) is connectionless and faster, but data can be lost or arrive out of sequence.
