# 🟢 Standard: String Escaping [CORE]

## Definition
C++ supports standard C-style escapes and adds **Raw String Literals** to handle complex strings (like regex or paths) without double-escaping.

## 1. Legacy Way (C++11 / C++17)
Standard escapes and basic raw strings.

```cpp
#include <iostream>

int main() {
    std::cout << "Line\n"; // \n = Newline
    
    // Raw String: R"( ... )"
    std::cout << R"(C:\Path\To\File)" << "\n"; 
    // Output: C:\Path\To\File
    return 0;
}
```

## 2. Modern Way (C23)
Universal character names and modern Unicode literals.

```cpp
#include <iostream>

int main() {
    // Unicode literal
    std::cout << "Rocket: \U0001F680\n"; // Output: Rocket: 🚀
    
    // Raw strings with custom delimiters
    std::cout << R"delimiter(Text with "quotes")delimiter" << "\n";
    // Output: Text with "quotes"
    return 0;
}
```

# The Logic Bridge
// Logic: Escape sequences are processed by the compiler's lexer. Raw strings tell the lexer to ignore everything until the closing delimiter, treating backslashes as literal characters.
