# 04 - Structs Base (CORE - Hub)

Definition: In C++, a `struct` is identical to a `class` except that its members are `public` by default. It is the primary gateway to Procedural Programming when used as a "Plain Old Data" (POD) container to group related variables.

## Deep-Dive Reference
For modular procedural architecture:
- [Procedural Mechanisms](./procedural/35-procedural-mechanisms.md)

---

## 1. Legacy Way (C++11 / C++17)
Standard definition and initialization.

```cpp
#include <iostream>

struct Config {
    int port;
    const char* host;
};

int main() {
    Config c = {80, "localhost"}; // Aggregate initialization
    std::cout << c.host << ":" << c.port << "\n"; // Output: localhost:80
    return 0;
}
```

## 2. Modern Way (C++23)
Using **Designated Initializers** (C++20) for clearer data grouping.

```cpp
#include <iostream>

struct Config {
    int port;
    const char* host;
};

int main() {
    // Clearer procedural initialization
    Config c = { .port = 443, .host = "127.0.0.1" };
    std::cout << c.port << "\n"; // Output: 443
    return 0;
}
```

# The Logic Bridge
// Logic: Structs in C++ provide a zero-cost way to group data. Unlike classes, they are typically used for simple data bags where encapsulation is not required, making them the standard choice for procedural data structures.
