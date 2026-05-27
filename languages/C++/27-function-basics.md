# 🟢 Standard: Function Basics [CORE]

## Definition
Reusable logic blocks. C++ supports function overloading (multiple functions with the same name but different parameters).

## 1. Legacy Way (C++11 / C++17)
Standard declaration and overloading.

```cpp
#include <iostream>

void print(int x) { std::cout << "Int: " << x << "\n"; }
void print(double x) { std::cout << "Double: " << x << "\n"; }

int main() {
    print(10);  // Output: Int: 10
    print(3.14); // Output: Double: 3.14
    return 0;
}
```

## 2. Modern Way (C23)
Using abbreviated function templates (C++20).

```cpp
#include <iostream>

// Abbreviated template: auto in parameter
void print(auto x) {
    std::cout << "Val: " << x << "\n";
}

int main() {
    print(10);   // Output: Val: 10
    print(3.14); // Output: Val: 3.14
    return 0;
}
```

# The Logic Bridge
// Logic: Function overloading is resolved at compile-time (Static Dispatch). The compiler "mangles" the names to distinguish between them in the final binary (e.g., `_Z5printi` vs `_Z5printd`).
