# 🔵 Standard: Multi-File Projects [PRO]

## Definition
Splitting code into Headers and Source files. Modern C++20 adds **Modules** (`import`) to replace the text-pasting `#include` system.

## 1. Legacy Way (C++11 / C++17)
Using Headers with `#include` and guards.

```cpp
// --- utils.h ---
#pragma once
int add(int a, int b);

// --- utils.cpp ---
#include "utils.h"
int add(int a, int b) { return a + b; }

// --- main.cpp ---
#include <iostream>
#include "utils.h"

int main() {
    std::cout << add(5, 5) << "\n"; // Output: 10
    return 0;
}
```

## 2. Modern Way (C23)
Using **C++20 Modules** for faster, isolated compilation.

```cpp
// --- math.cppm (Module interface) ---
export module math;
export int add(int a, int b) { return a + b; }

// --- main.cpp ---
import math; // Modern import
#include <iostream>

int main() {
    std::cout << add(5, 5) << "\n"; // Output: 10
    return 0;
}
```

# The Logic Bridge
// Logic: `#include` is a recursive text-copy operation by the preprocessor. Modules are pre-compiled into a binary format, providing isolated macro-free namespaces and significantly faster build times.
