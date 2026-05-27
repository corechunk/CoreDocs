# 🏛️ Master C++ Reference: The Core Foundation

**Purpose:** A high-density, one-shot reference for foundational C++ logic. This file mirrors the evolution from established standards (C++11/C++17) to the modern **C++23** standard.

---

## Toolchain Installation [01]

### Definition
Environment setup for compiling and linking C++ code.

### 1. Legacy Way (System-Wide)
```bash
# Arch/Debian
sudo pacman -S base-devel
sudo apt install build-essential

# Verify
g++ --version // Output: g++ (GCC) 13.x.x
```

### 2. Modern Way (Mise)
```bash
# Project-local version locking
mise use gcc@13.2.0

# Verify
g++ --version // Output: g++ (GCC) 13.2.0
```

# The Logic Bridge
// Logic: Version locking ensures build reproducibility across different developer machines and CI/CD pipelines.

---

## Compilation Ritual [02]

### Definition
Transforming source to binary with standard enforcement.

### 1. Legacy Way (C++11)
```bash
g++ -std=c++11 main.cpp -o app
./app // Output: (Result)
```

### 2. Modern Way (C++23)
```bash
g++ -std=c++23 -Wall -Wextra -Werror -Wpedantic main.cpp -o app
./app # Output: (Result)
```

# The Logic Bridge
// Logic: Modern flags enable maximum compiler diagnostics, catching logical flaws during the translation phase.

---

## Tokens & Lexemes [04]

### Definition
The building blocks of C++ grammar.

### 1. Legacy Way (Explicit)
```cpp
#include <iostream>
int main() {
    int age = 25;
    std::cout << age << "\n"; // Output: 25
    return 0;
}
```

### 2. Modern Way (Deducted)
```cpp
#include <iostream>
int main() {
    auto age = 25;
    std::cout << age << "\n"; // Output: 25
    return 0;
}
```

# The Logic Bridge
// Logic: Type deduction (`auto`) happens at compile-time. The compiler analyzes the literal `25` to categorize the token as an integer.

---

## Keywords & Standards [05]

### Definition
The reserved words and language evolution.

### 1. Legacy Way (C++11)
```cpp
#include <iostream>
int main() {
    int* p = nullptr; // C++11 keyword
    std::cout << (p == nullptr) << "\n"; // Output: 1
    return 0;
}
```

### 2. Modern Way (C++23)
```cpp
#include <iostream>
int main() {
    constexpr int x = 10; // Compile-time constant
    bool active = true;
    std::cout << x << " " << active << "\n"; // Output: 10 1
    return 0;
}
```

# The Logic Bridge
// Logic: Standards define the grammar. Newer standards add keywords that move runtime work to compile-time (like `constexpr`).

---

## Variables & Constants [08]

### Definition
Mutable vs Immutable storage.

### 1. Legacy Way (const)
```cpp
#include <iostream>
int main() {
    const int x = 10;
    std::cout << x << "\n"; // Output: 10
    return 0;
}
```

### 2. Modern Way (constexpr)
```cpp
#include <iostream>
int main() {
    constexpr auto x = 10;
    std::cout << x << "\n"; // Output: 10
    return 0;
}
```

# The Logic Bridge
// Logic: `const` is a runtime read-only promise. `constexpr` is a compile-time value.

---

## Data Types [09]

### Definition
Interpretation of binary memory.

### 1. Legacy Way (Explicit)
```cpp
#include <iostream>
int main() {
    int i = 10;
    bool b = true;
    std::cout << i << " " << b << "\n"; // Output: 10 1
    return 0;
}
```

### 2. Modern Way (auto)
```cpp
#include <iostream>
int main() {
    auto i = 10;
    auto b = true;
    std::cout << i << " " << b << "\n"; // Output: 10 1
    return 0;
}
```

# The Logic Bridge
// Logic: Type deduction simplifies code without losing the performance of static typing.

---

## String Escaping [10]

### Definition
Invisible and raw string representation.

### 1. Legacy Way (Standard)
```cpp
#include <iostream>
int main() {
    std::cout << "Line\n"; // Output: Line
    return 0;
}
```

### 2. Modern Way (Raw)
```cpp
#include <iostream>
int main() {
    std::cout << R"(C:\Path)" << "\n"; // Output: C:\Path
    return 0;
}
```

# The Logic Bridge
// Logic: Raw string literals skip escape-processing, vital for regex and paths.

---

## Interpolation (Formatting) [11]

### Definition
Variable substitution in strings.

### 1. Legacy Way (Streams)
```cpp
#include <iostream>
int main() {
    std::cout << "Val: " << 10 << "\n"; // Output: Val: 10
    return 0;
}
```

### 2. Modern Way (std::print)
```cpp
#include <print>
int main() {
    std::print("Val: {}\n", 10); // Output: Val: 10
    return 0;
}
```

# The Logic Bridge
// Logic: `std::print` uses compile-time formatting strings, faster than iostreams.

---

## Scope & Lifetime [12]

### Definition
Visibility and RAII automatic destruction.

### 1. Legacy Way (Block)
```cpp
#include <iostream>
#include <string>
int main() {
    { std::string s = "Hi"; }
    std::cout << "Gone\n"; // Output: Gone
    return 0;
}
```

### 2. Modern Way (Init)
```cpp
#include <iostream>
int main() {
    if (auto s = true; s) { std::cout << "OK\n"; } // Output: OK
    return 0;
}
```

# The Logic Bridge
// Logic: RAII ensures resources are released the moment the owner goes out of scope.

---

## Operators [17]

### Definition
Symbols for computation.

### 1. Legacy Way (Arithmetic)
```cpp
#include <iostream>
int main() {
    std::cout << 5 + 5 << "\n"; // Output: 10
    return 0;
}
```

### 2. Modern Way (Spaceship)
```cpp
#include <iostream>
#include <compare>
int main() {
    auto res = (5 <=> 10);
    if (res < 0) std::cout << "Less\n"; // Output: Less
    return 0;
}
```

# The Logic Bridge
// Logic: The spaceship operator provides all comparison results in one CPU step.

---

## Conditionals [23]

### Definition
Branching logic.

### 1. Legacy Way (Standard)
```cpp
#include <iostream>
int main() {
    if (true) std::cout << "Yes\n"; // Output: Yes
    return 0;
}
```

### 2. Modern Way (Attributes)
```cpp
#include <iostream>
int main() {
    switch(1) { [[likely]] case 1: std::cout << "Yes\n"; } // Output: Yes
    return 0;
}
```

# The Logic Bridge
// Logic: Attributes like `[[likely]]` help the compiler optimize the instruction pipeline.

---

## Function Engine [27]

### Definition
Reusable logic units.

### 1. Legacy Way (Overloading)
```cpp
#include <iostream>
void p(int x) { std::cout << x << "\n"; }
int main() { p(10); return 0; } // Output: 10
```

### 2. Modern Way (Abbreviated)
```cpp
#include <iostream>
void p(auto x) { std::cout << x << "\n"; }
int main() { p(10); return 0; } // Output: 10
```

# The Logic Bridge
// Logic: Abbreviated templates simplify generic logic without manual template syntax.

---

## Arrays [32]

### Definition
Sequential memory blocks.

### 1. Legacy Way (std::vector)
```cpp
#include <iostream>
#include <vector>
int main() {
    std::vector<int> v = {1};
    std::cout << v[0] << "\n"; // Output: 1
    return 0;
}
```

### 2. Modern Way (Ranges)
```cpp
#include <iostream>
#include <vector>
#include <ranges>
int main() {
    std::vector v = {1, 2};
    for (auto i : v | std::views::reverse) std::cout << i << " "; // Output: 2 1
    return 0;
}
```

# The Logic Bridge
// Logic: Ranges provide lazy views of memory, avoiding physical copies during transformation.

---

## Structs [34]

### Definition
Public-by-default data groupings.

### 1. Legacy Way (Standard)
```cpp
#include <iostream>
struct U { int id; };
int main() { U u = {1}; std::cout << u.id << "\n"; return 0; } // Output: 1
```

### 2. Modern Way (Designated)
```cpp
#include <iostream>
struct U { int id; };
int main() { U u = {.id = 1}; std::cout << u.id << "\n"; return 0; } // Output: 1
```

# The Logic Bridge
// Logic: Structs are primarily used for memory-aligned data packets (POD types).

---

## I/O Streams [45]

### Definition
Standard interaction paths.

### 1. Legacy Way (cout)
```cpp
#include <iostream>
int main() { std::cout << "Hi\n"; return 0; } // Output: Hi
```

### 2. Modern Way (print)
```cpp
#include <print>
int main() { std::print("Hi\n"); return 0; } // Output: Hi
```

# The Logic Bridge
// Logic: `std::print` bypasses the heavy virtual call overhead of iostreams.

---

## Error Handling [49]

### Definition
Managing runtime failures.

### 1. Legacy Way (Exceptions)
```cpp
#include <iostream>
int main() {
    try { throw 1; } catch(...) { std::cout << "Err\n"; } // Output: Err
    return 0;
}
```

### 2. Modern Way (Expected)
```cpp
#include <iostream>
#include <expected>
int main() {
    std::expected<int, int> res = std::unexpected(1);
    if (!res) std::cout << "Err\n"; // Output: Err
    return 0;
}
```

# The Logic Bridge
// Logic: `std::expected` provides functional error handling without the stack-unwinding cost.
