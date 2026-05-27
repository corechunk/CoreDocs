# 🟢 Standard: Passing Mechanisms [CORE]

## Definition
C++ adds **References** to C's value/pointer logic. References are aliases for existing variables, safer and cleaner than pointers.

## 1. Legacy Way (C++11 / C++17)
Passing by Value vs Reference.

```cpp
#include <iostream>

void inc_val(int x) { x++; }    // Copy
void inc_ref(int& x) { x++; }   // Alias (Original)

int main() {
    int a = 10, b = 10;
    inc_val(a);
    inc_ref(b);
    std::cout << a << " " << b << "\n"; // Output: 10 11
    return 0;
}
```

## 2. Modern Way (C23)
Using **Perfect Forwarding** and `std::move` (C++11/20).

```cpp
#include <iostream>
#include <utility>

void process(int&& x) { std::cout << "Moved\n"; } // Rvalue ref

int main() {
    int a = 10;
    process(std::move(a)); // Output: Moved
    return 0;
}
```

# The Logic Bridge
// Logic: References are implemented by the compiler as constant pointers (`int* const`), but they are automatically dereferenced and cannot be null, making them much safer than raw pointers.
