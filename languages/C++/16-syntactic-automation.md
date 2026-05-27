# 🔴 Standard: Syntactic Automation [SYSTEMS]

## Definition
Syntactic automation in C++ is driven by the **Template Engine**. It allows the compiler to generate specialized code for any data type, enabling "Type-Safe Generics."

## 1. Legacy Way (C++11 / C++17)
Basic function templates.

```cpp
#include <iostream>

// Template: Compiles a version for every used type
template <typename T>
T add(T a, T b) { return a + b; }

int main() {
    std::cout << add(5, 5) << "\n";       // Output: 10
    std::cout << add(3.5, 2.5) << "\n";   // Output: 6
    return 0;
}
```

## 2. Modern Way (C23)
Using **Concepts** (C++20/23) to constrain templates and provide better error messages.

```cpp
#include <iostream>
#include <concepts> // C++20

// Constrained Template: Only works for numeric types
template <std::number T> // Requires a concept
T add(T a, T b) { return a + b; }

int main() {
    // Abbreviated Function Template (C++20)
    auto sub = [](std::arithmetic auto a, std::arithmetic auto b) {
        return a - b;
    };

    std::cout << add(5, 5) << "\n"; // Output: 10
    return 0;
}
```

## Deep-Dive Reference
For meta-programming and compile-time logic:
- [Templates](./data-type/templates.md) | [Concepts](./data-type/concepts.md) | [Type Traits](./data-type/type-traits.md)

# The Logic Bridge
// Logic: Templates are a form of "Compile-Time Polymorphism." The compiler physically writes a new version of the function in the binary for every unique type it encounters.
