# 🔴 Standard: Memory Management [SYSTEMS]

## Definition
C++ memory management has moved from manual `new`/`delete` to **Smart Pointers** (RAII), which eliminate memory leaks by tying memory ownership to object scope.

## 1. Legacy Way (C++11 / C++17)
Manual allocation with `new` (Not recommended in modern C++).

```cpp
#include <iostream>

int main() {
    int* ptr = new int(10);
    
    if (ptr != nullptr) {
        std::cout << "Val: " << *ptr << "\n"; // Output: Val: 10
        delete ptr; // Must manually delete
    }
    return 0;
}
```

## 2. Modern Way (C23)
Using **`std::unique_ptr`** and **`std::make_unique`** (C++14).

```cpp
#include <iostream>
#include <memory>

int main() {
    // unique_ptr: Automatically deletes memory on scope exit
    auto ptr = std::make_unique<int>(10);

    if (ptr) {
        std::cout << "Val: " << *ptr << "\n"; // Output: Val: 10
    }
    // Delete called automatically here
    return 0;
}
```

## Deep-Dive Reference
For manual lifecycles and addressing:
- [Stack vs Heap](./memory/stack-heap.md) | [Allocators](./memory/allocation.md) | [Pointer Math](./memory/pointer-arithmetic.md)

# The Logic Bridge
// Logic: `new` calls the allocator and the constructor. `std::unique_ptr` is a wrapper struct that calls `delete` in its destructor, ensuring the memory is released even if an exception occurs.
