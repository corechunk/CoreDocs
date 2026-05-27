# 🔭 STL Views & Spans (Fast Access) - Master Reference

## 1. The Objective
Views and Spans are **Non-owning** references to existing data. They allow you to write functions that work with any contiguous data (Vector, Array, C-array) without copying or needing templates.

---

## 2. Visual Logic
### The View Window
```text
Original Vector: [ A | B | C | D | E ]
                        ^   ^
                        |---|
                    std::span (A "Window" looking at C, D)
```

---

## 3. # The Logic Bridge (Key Points)

- **`std::string_view` (C++17):** A replacement for `const std::string&`. It doesn't copy the string; it just stores a pointer and a length.
- **`std::span` (C++20):** A replacement for `(T* ptr, size_t size)`. It works for any contiguous container.
- **Zero-Copy Performance:** Using views allows you to "slice" data (like taking the first 10 elements of a vector) without allocating new memory.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Exhaustive Usage)

```cpp
#include <iostream>
#include <vector>
#include <string_view>
#include <span>

// Function works for ANY contiguous container of ints
void printSpan(std::span<const int> s) {
    for (int x : s) std::cout << x << " ";
    std::cout << "\n";
}

int main() {
    // 1. std::string_view
    std::string s = "Hello World";
    std::string_view sv = s;
    std::string_view sub = sv.substr(0, 5); // "Hello" (No copy!)

    // 2. std::span
    std::vector v = {1, 2, 3, 4, 5};
    int arr[] = {10, 20, 30};

    printSpan(v);             // Works with vector
    printSpan(arr);           // Works with C-array
    printSpan({v.data(), 3}); // Works with a sub-slice

    return 0;
}
```

---
[➔ Back to STL Hub](00-stl-overview.md)
