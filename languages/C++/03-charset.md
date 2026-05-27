# 🔴 Standard: Charset & Encoding [SYSTEMS]

## Definition
C++ has evolved from basic 8-bit characters to native Unicode support. UTF-8 is the modern industry standard for C++ character handling.

## 1. Legacy Way (C++11 / C++17)
Using `char` for ASCII and `std::string` for byte-sequences.

```cpp
#include <iostream>

int main() {
    char a = 'A';
    const char* s = "Hello";
    
    std::cout << "Char: " << a << "\n"; // Output: Char: A
    std::cout << "Str: " << s << "\n";   // Output: Str: Hello
    return 0;
}
```

## 2. Modern Way (C++23)
Native support for Unicode literals (`u8`, `u`, `U`) and `std::u8string`.

```cpp
#include <iostream>

int main() {
    // u8 prefix for UTF-8 (C++20/23 standard)
    const char* emoji = "🚀"; 
    
    std::cout << "Emoji: " << emoji << "\n"; // Output: Emoji: 🚀
    
    // C++23 allows auto for string literals
    auto msg = "Hello"; 
    std::cout << msg << "\n"; // Output: Hello
    return 0;
}
```

# The Logic Bridge
// Logic: Character literals are translated into numeric code points. Modern C++ (C++20+) guarantees that `char` can hold any UTF-8 code unit if the execution charset is UTF-8.
