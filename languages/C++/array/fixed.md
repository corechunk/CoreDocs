# 🔴 Standard: Fixed-Size Arrays [SYSTEMS]

## Definition
`std::array` (C++11) provides a type-safe, fixed-size wrapper around raw arrays. It resides entirely on the Stack and does not decay to pointers automatically.

## 1. Legacy Way (C++11 / C++17)
Standard usage.

```cpp
#include <iostream>
#include <array>

int main() {
    std::array<int, 3> arr = {1, 2, 3};
    std::cout << "Size: " << arr.size() << "\n"; // Output: Size: 3
    return 0;
}
```

## 2. Modern Way (C23)
Using `std::array` with `constexpr` and `auto`.

```cpp
#include <iostream>
#include <array>

int main() {
    constexpr auto arr = std::array{1, 2, 3}; // CTAD
    static_assert(arr.size() == 3);
    
    std::cout << arr[0] << "\n"; // Output: 1
    return 0;
}
```

# The Logic Bridge
// Logic: `std::array` is a "Zero-Overhead" abstraction. Its memory layout is identical to a raw `T[N]`, but it provides a safer interface and supports STL algorithms.
