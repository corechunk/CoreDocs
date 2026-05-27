# 🟢 Standard: Type Casting [CORE]

## Definition
Converting types. C++ introduces specific cast operators that are safer than C-style casts.

## 1. Legacy Way (C++11 / C++17)
Using `static_cast` for safe conversions.

```cpp
#include <iostream>

int main() {
    double d = 3.14;
    int i = static_cast<int>(d);
    
    std::cout << i << "\n"; // Output: 3
    return 0;
}
```

## 2. Modern Way (C23)
Mirroring task with `auto`.

```cpp
#include <iostream>

int main() {
    auto d = 3.14;
    auto i = static_cast<int>(d);

    std::cout << i << "\n"; // Output: 3
    return 0;
}
```

# The Logic Bridge
// Logic: `static_cast` is checked at compile-time. It ensures that the types are compatible (e.g., int and double) before allowing the bit-pattern conversion.
