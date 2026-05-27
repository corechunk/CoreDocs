# 🔵 Standard: Pattern Matching [PRO]

## Definition
Pattern matching in C++ is handled by the `std::regex` library (C++11), allowing for complex string validation and extraction.

## 1. Legacy Way (C++11 / C++17)
Standard `std::regex` usage for digit matching.

```cpp
#include <iostream>
#include <string>
#include <regex>

int main() {
    std::string text = "ID: 12345";
    std::regex pattern("[0-9]+");
    
    if (std::regex_search(text, pattern)) {
        std::cout << "Found Digits\n"; // Output: Found Digits
    }
    return 0;
}
```

## 2. Modern Way (C23)
Using **CTRE** (Compile-Time Regular Expressions) or modern raw strings for cleaner patterns.

```cpp
#include <iostream>
#include <string>
#include <regex>

int main() {
    // auto and raw strings for cleaner regex syntax
    auto text = "ID: 12345";
    auto pattern = std::regex(R"(\d+)"); 
    
    if (std::regex_search(text, pattern)) {
        std::cout << "Found Digits\n"; // Output: Found Digits
    }
    return 0;
}
```

# The Logic Bridge
// Logic: `std::regex` compiles the pattern string into a state machine at runtime. Modern C++ alternatives like CTRE perform this compilation during build-time, making execution nearly instantaneous.
