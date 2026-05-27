# 🟢 Standard: Tokens & Lexemes [CORE]

## Definition
Tokens are the smallest meaningful components of C++ code. Lexemes are the actual characters forming them.

## 1. Legacy Way (C++11 / C++17)
Identifying tokens in standard declarations.

```cpp
#include <iostream>

int main() {
    int age = 25; // Tokens: [int] [age] [=] [25] [;]
    std::cout << age << "\n"; // Output: 25
    return 0;
}
```

## 2. Modern Way (C++23)
Identifying tokens involving modern keywords and type deduction.

```cpp
#include <iostream>

int main() {
    auto age = 25; // Tokens: [auto] [age] [=] [25] [;]
    std::cout << age << "\n"; // Output: 25
    return 0;
}
```

# The Logic Bridge
// Logic: The Lexer strips whitespace and categorizes text into tokens, which the Parser then uses to build the Abstract Syntax Tree (AST).
