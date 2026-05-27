# 🟢 Standard: Assignment Operators [CORE]

## Definition
Storing values and performing compound math.

## 1. Legacy Way (C++11 / C++17)
Standard and compound assignment.

```cpp
#include <iostream>

int main() {
    int x = 10;
    x += 5; 
    std::cout << x << "\n"; // Output: 15
    return 0;
}
```

## 2. Modern Way (C23)
Identical syntax, mirrored task.

```cpp
#include <iostream>

int main() {
    auto x = 10;
    x += 5;
    std::cout << x << "\n"; // Output: 15
    return 0;
}
```

# The Logic Bridge
// Logic: Compound assignments like `+=` are atomic operations for primitive types, reducing the overhead of intermediate register copies.
