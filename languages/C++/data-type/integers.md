# 🔴 Standard: Integer Deep-Dive [SYSTEMS]

## Definition
Integer types in C++ follow the same width hierarchy as C, with C++ adding binary literals and digit separators for better readability in systems code.

## 1. Legacy Way (C++11 / C++17)
Standard widths and Hex-based bitmasks.

```cpp
#include <iostream>
#include <climits>

int main() {
    short a = 10;
    int b = 100;
    long long c = 1000;

    int mask = 0x0C; // Binary: 1100

    std::cout << "Max Int: " << INT_MAX << "\n"; // Output: Max Int: 2147483647
    return 0;
}
```

## 2. Modern Way (C23)
Using binary literals and digit separators.

```cpp
#include <iostream>
#include <climits>

int main() {
    short a = 10;
    int b = 100;
    long long c = 1_000_000; // Digit separator

    // Binary Literal (C++14 Native)
    int mask = 0b1100; 

    std::cout << "Max Int: " << INT_MAX << "\n"; // Output: Max Int: 2147483647
    return 0;
}
```

# The Logic Bridge
// Logic: Integer literals (`0b`, `0x`) are syntactic sugar for the same binary values. The CPU performs the same arithmetic regardless of how the number was written in source code.
