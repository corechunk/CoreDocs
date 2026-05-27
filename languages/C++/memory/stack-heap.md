# 🔴 Standard: Stack vs. Heap [SYSTEMS]

## Definition
Memory locations. Stack is local and fast; Heap is global and large.

## 1. Legacy Way (C++11 / C++17)
```cpp
#include <iostream>

int main() {
    int s = 10; // Stack
    int* h = new int(20); // Heap
    std::cout << "S: " << s << " H: " << *h << "\n"; // Output: S: 10 H: 20
    delete h;
    return 0;
}
```

## 2. Modern Way (C23)
```cpp
#include <iostream>
#include <memory>

int main() {
    auto s = 10;
    auto h = std::make_unique<int>(20);
    std::cout << "S: " << s << " H: " << *h << "\n"; // Output: S: 10 H: 20
    return 0;
}
```

# The Logic Bridge
// Logic: The Stack is managed by the CPU's stack pointer. The Heap is managed by the OS memory manager via a free-list or bitmap of available pages.
