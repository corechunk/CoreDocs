# 🔴 Standard: Multi-Dimensional Arrays [SYSTEMS]

## Definition
Grids in C++ can be raw `[][]`, `std::vector<std::vector>`, or the modern **`std::mdspan`** (C++23) for non-owning views of multi-dimensional data.

## 1. Legacy Way (C++11 / C++17)
Nested vectors (Heavyweight).

```cpp
#include <iostream>
#include <vector>

int main() {
    std::vector<std::vector<int>> matrix = {
        {1, 2},
        {3, 4}
    };
    
    std::cout << matrix[1][0] << "\n"; // Output: 3
    return 0;
}
```

## 2. Modern Way (C23)
Using `std::mdspan` to view a flat array as a 2D grid.

```cpp
#include <iostream>
#include <vector>
#include <mdspan> // C++23

int main() {
    std::vector<int> data = {1, 2, 3, 4};
    // View flat data as 2x2 grid
    auto ms = std::mdspan(data.data(), 2, 2);

    std::cout << ms[1, 0] << "\n"; // Output: 3
    return 0;
}
```

# The Logic Bridge
// Logic: `std::mdspan` uses mapping functions to translate 2D coordinates `[i, j]` into a flat index `i * cols + j` at compile-time, providing multidimensional logic without heap overhead.
