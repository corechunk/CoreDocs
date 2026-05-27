# 🟢 Standard: Conditionals [CORE]

## Definition
Conditional branching using `if` and `switch`. C++17 added **Init-Statements**, allowing variables to be scoped only to the conditional block.

## 1. Legacy Way (C++11)
Standard `if` and `switch`.

```cpp
#include <iostream>

int main() {
    int val = 1;

    if (val == 1) {
        std::cout << "One\n"; // Output: One
    }

    switch (val) {
        case 1: std::cout << "One\n"; break; // Output: One
    }
    return 0;
}
```

## 2. Modern Way (C23)
Using C++17/20/23 init-statements and attributes.

```cpp
#include <iostream>

int main() {
    // Init-statement: Scope limited to IF
    if (auto val = 1; val == 1) {
        std::cout << "One\n"; // Output: One
    }

    auto x = 1;
    switch (x) {
        case 1: std::cout << "One\n"; break; // Output: One
        [[likely]] case 2: break; // Optimization hint
    }
    return 0;
}
```

## Deep-Dive Reference
For nested logic and fall-through:
- [if-else.md](./control/if-else.md) | [switch.md](./control/switch.md)

# The Logic Bridge
// Logic: `switch` statements are optimized by the compiler into Jump Tables. The `[[likely]]` attribute tells the compiler to optimize the machine code for that specific branch path.
