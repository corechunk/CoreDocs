# 🟢 Standard: Switch Case [CORE]

## Definition
Branching based on discrete constant values. C++ adds attributes to manage fall-through safety.

## 1. Legacy Way (C++11 / C++17)
Standard usage.

```cpp
#include <iostream>

int main() {
    int code = 1;
    switch (code) {
        case 1: std::cout << "One\n"; break; // Output: One
        default: std::cout << "Other\n";
    }
    return 0;
}
```

## 2. Modern Way (C23)
Using `[[fallthrough]]` and modern init-statements.

```cpp
#include <iostream>

int main() {
    switch (auto code = 1; code) {
        case 1: 
            std::cout << "One\n"; // Output: One
            [[fallthrough]];
        case 2: 
            std::cout << "Two\n"; // Output: Two
            break;
    }
    return 0;
}
```

# The Logic Bridge
// Logic: `[[fallthrough]]` is a metadata attribute that suppresses compiler warnings about missing `break` statements, documenting intentional logic flow.
