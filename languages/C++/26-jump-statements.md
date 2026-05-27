# 🔵 Standard: Jump Statements [PRO]

## Definition
Interrupting flow with `break`, `continue`, and `goto`.

## 1. Legacy Way (C++11 / C++17)
Standard interruption.

```cpp
#include <iostream>

int main() {
    for (int i = 0; i < 5; i++) {
        if (i == 1) continue;
        if (i == 3) break;
        std::cout << i << " ";
    }
    // Output: 0 2
    return 0;
}
```

## 2. Modern Way (C23)
Identical syntax, mirrored task.

```cpp
#include <iostream>

int main() {
    for (auto i = 0; i < 5; i++) {
        if (i == 1) continue;
        if (i == 3) break;
        std::cout << i << " ";
    }
    // Output: 0 2
    return 0;
}
```

# The Logic Bridge
// Logic: `break` and `continue` only affect the innermost loop. They are structured jumps that the compiler uses to skip to the end or the next iteration of the loop's logic block.
