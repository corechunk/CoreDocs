# 🔵 Standard: Native Strings [PRO]

## Definition
C++ provides `std::string` for dynamic, memory-managed strings and `std::string_view` (C++17) for non-owning, high-performance string slices.

## 1. Legacy Way (C++11)
Using `std::string` and manual slicing with `substr`.

```cpp
#include <iostream>
#include <string>

int main() {
    std::string s = "C++ Strings";
    
    // Manual Copy/Slice
    std::string sub = s.substr(0, 3);
    
    std::cout << "Full: " << s << "\n";   // Output: Full: C++ Strings
    std::cout << "Sub: " << sub << "\n";  // Output: Sub: C++
    return 0;
}
```

## 2. Modern Way (C23)
Using `std::string_view` to avoid unnecessary memory allocations.

```cpp
#include <iostream>
#include <string>
#include <string_view> // C++17

int main() {
    // string_view: No memory allocation, just a pointer + length
    std::string_view s = "C++ Strings";
    
    // O(1) Slicing
    auto sub = s.substr(0, 3); 
    
    std::cout << "Full: " << s << "\n";   // Output: Full: C++ Strings
    std::cout << "Sub: " << sub << "\n";  // Output: Sub: C++
    return 0;
}
```

# The Logic Bridge
// Logic: `std::string` owns its memory on the Heap. `std::string_view` simply points to an existing buffer, eliminating the overhead of copying bytes when performing read-only operations.
