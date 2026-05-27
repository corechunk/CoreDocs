# 🛡️ STL Vocabulary Types - Master Reference

## 1. The Objective
Vocabulary types express **Intent**. They are designed to replace "ambiguous" coding patterns (like using NULL pointers for missing values or using -1 for errors) with type-safe, standard structures.

---

## 2. Visual Logic
- **`std::optional`:** A box that is either `[ Empty ]` or `[ Value ]`.
- **`std::variant`:** A safe "Union" that can hold `[ Type A ]` OR `[ Type B ]`.
- **`std::any`:** A box that can hold `[ Anything ]`.

---

## 3. # The Logic Bridge (Key Points)

- **`std::optional` (C++17):** Use when a function might not return a result. It forces the caller to check `.has_value()`, preventing null dereference crashes.
- **`std::variant` (C++17):** A type-safe version of a C-union. It knows which type it currently holds and prevents you from accessing the wrong one.
- **`std::expected` (C++23):** A specialized version of variant for error handling. It holds either the `[ Result ]` OR an `[ Error ]`.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Exhaustive Usage)

```cpp
#include <iostream>
#include <optional>
#include <variant>
#include <string>

// 1. Optional Result
std::optional<int> divide(int a, int b) {
    if (b == 0) return std::nullopt;
    return a / b;
}

int main() {
    // --- USING OPTIONAL ---
    auto res = divide(10, 0);
    if (res) std::cout << "Result: " << *res << "\n";
    else std::cout << "Error: Division by zero\n";

    // --- USING VARIANT ---
    std::variant<int, std::string> v;
    v = 10;
    v = "Hello";
    
    if (auto p = std::get_if<std::string>(&v)) {
        std::cout << "It's a string: " << *p << "\n";
    }

    return 0;
}
```

---
[➔ Back to STL Hub](00-stl-overview.md)
