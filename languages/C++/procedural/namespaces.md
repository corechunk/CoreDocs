# Namespaces (PRO)

Definition: A declarative region that provides a scope to identifiers (names of types, functions, variables, etc) inside it.

## 1. Legacy Way (C++11 / C++17)
Standard nested namespaces.

```cpp
namespace App {
    namespace Detail {
        void init() { }
    }
}
```

## 2. Modern Way (C++23)
Using **Compact Nested Namespaces** (C++17) and **Anonymous Namespaces**.

```cpp
namespace App::Detail {
    void start() { }
}

namespace {
    // Internal linkage: Only visible in this file
    int local_counter = 0;
}
```

# The Logic Bridge
// Logic: Namespaces resolve the "Global Namespace Pollution" problem. Symbols inside an anonymous namespace have internal linkage, meaning they are not exported to the linker, reducing binary size and preventing collision across translation units.
