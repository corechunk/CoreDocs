# 🟢 Standard: Error Handling [CORE]

## Definition
C++ uses **Exceptions** (`try/catch`) for runtime errors and the modern **`std::expected`** (C++23) for value-based error signaling.

## 1. Legacy Way (C++11 / C++17)
Standard Exception handling.

```cpp
#include <iostream>
#include <stdexcept>

int main() {
    try {
        throw std::runtime_error("Fail");
    } catch (const std::exception& e) {
        std::cout << e.what() << "\n"; // Output: Fail
    }
    return 0;
}
```

## 2. Modern Way (C23)
Using **`std::expected`** (C++23) for explicit, non-throwing errors.

```cpp
#include <iostream>
#include <expected> // C++23
#include <string>

std::expected<int, std::string> get_val(bool fail) {
    if (fail) return std::unexpected("Fail");
    return 10;
}

int main() {
    auto res = get_val(true);
    if (!res) {
        std::cout << res.error() << "\n"; // Output: Fail
    }
    return 0;
}
```

# The Logic Bridge
// Logic: Exceptions use "Stack Unwinding," which has significant overhead as it searches for a handler. `std::expected` is a variant-based result type that stays in a register, making it much faster for common error paths.
