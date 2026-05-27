# 🔴 Standard: Allocators [SYSTEMS]

## Definition
The lifecycle of heap objects via `new`, `delete`, and STL allocators.

## 1. Legacy Way (C++11 / C++17)
Manual new/delete.

```cpp
#include <iostream>

int main() {
    int* arr = new int[5];
    arr[0] = 1;
    std::cout << arr[0] << "\n"; // Output: 1
    delete[] arr;
    return 0;
}
```

## 2. Modern Way (C23)
Using smart pointers for arrays.

```cpp
#include <iostream>
#include <memory>

int main() {
    auto arr = std::make_unique<int[]>(5);
    arr[0] = 1;
    std::cout << arr[0] << "\n"; // Output: 1
    return 0;
}
```

# The Logic Bridge
// Logic: `new[]` stores the number of elements in a hidden "Cookie" just before the array's memory address, so `delete[]` knows how many destructors to call.
