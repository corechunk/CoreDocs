# 🔴 Standard: Pointer Arithmetic [SYSTEMS]

## Definition
C++ supports C-style pointer arithmetic but encourages **Iterators** for safer traversal.

## 1. Legacy Way (C++11 / C++17)
Raw pointer increment.

```cpp
#include <iostream>

int main() {
    int arr[] = {1, 2};
    int* p = arr;
    std::cout << *p << " "; // Output: 1 
    p++;
    std::cout << *p << "\n"; // Output: 2
    return 0;
}
```

## 2. Modern Way (C23)
Using **Iterators** and `std::next`.

```cpp
#include <iostream>
#include <vector>
#include <iterator>

int main() {
    std::vector<int> v = {1, 2};
    auto it = v.begin();
    std::cout << *it << " "; // Output: 1
    it = std::next(it);
    std::cout << *it << "\n"; // Output: 2
    return 0;
}
```

# The Logic Bridge
// Logic: Iterators are objects that behave like pointers but can include bounds-checking. The compiler optimizes them back into raw pointer arithmetic in Release builds.
