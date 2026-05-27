# 🟢 Standard: Indefinite Iteration [CORE]

## Definition
Loops that continue while a condition is True. `while` and `do-while`.

## 1. Legacy Way (C++11 / C++17)
Standard usage.

```cpp
#include <iostream>

int main() {
    int i = 0;
    while (i < 1) {
        std::cout << "Step\n"; // Output: Step
        i++;
    }
    return 0;
}
```

## 2. Modern Way (C23)
Mirroring same task with `auto`.

```cpp
#include <iostream>

int main() {
    auto i = 0;
    while (i < 1) {
        std::cout << "Step\n"; // Output: Step
        i++;
    }
    return 0;
}
```

# The Logic Bridge
// Logic: `while` loops are "Top-tested"; the condition is checked before any code in the body executes. `do-while` is "Bottom-tested," ensuring the body runs at least once.
