# 🟢 Standard: Return Types [CORE]

## Definition
Functions can return values, references, or nothing (`void`). C++14 added automatic return type deduction.

## 1. Legacy Way (C++11)
Explicit return types.

```cpp
#include <iostream>

int add(int a, int b) {
    return a + b;
}

int main() {
    std::cout << add(5, 5) << "\n"; // Output: 10
    return 0;
}
```

## 2. Modern Way (C23)
Using `auto` return type and trailing return syntax.

```cpp
#include <iostream>

// auto return: Deducts from return statement (C++14)
auto add(int a, int b) {
    return a + b;
}

// Trailing return: Useful for complex template return types
auto sub(int a, int b) -> int {
    return a - b;
}

int main() {
    std::cout << add(5, 5) << "\n"; // Output: 10
    return 0;
}
```

# The Logic Bridge
// Logic: Automatic return type deduction occurs after the compiler has parsed the function body. It ensures the returned expression matches the expected result without manual type declarations.
