# 🟢 Standard: Comments & Metadata [CORE]

## Definition
Comments provide human documentation. Metadata (Attributes) provides instructions directly to the compiler.

## 1. Legacy Way (C++11 / C++17)
Standard single and multi-line comments.

```cpp
#include <iostream>

/* Multi-line Header */
int main() {
    int x = 10; // Single-line note
    std::cout << x << "\n"; // Output: 10
    return 0;
}
```

## 2. Modern Way (C++23)
Using **Attributes** (`[[ ]]`) to provide metadata to the compiler for optimization or safety.

```cpp
#include <iostream>

[[nodiscard]] int get_val() { return 10; }

int main() {
    int x = get_val(); // Metadata warns if return is ignored
    std::cout << x << "\n"; // Output: 10
    return 0;
}
```

# The Logic Bridge
// Logic: Comments are physically removed by the preprocessor. Attributes are preserved and used by the compiler's backend to generate specialized machine code or warnings.
