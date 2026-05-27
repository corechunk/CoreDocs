# 🔗 STL Iterators

## 1. The Objective
Iterators are the "Glue" of the STL. They provide a unified way to move through any container (Vector, List, Map) without needing to know how that container is implemented internally.

---

## 2. Visual Logic
### The Abstract Pointer
```text
Container: [ A | B | C | D ]
             ^           ^
             |           |
           begin()      end() (Points PAST the last element)
```

---

## 3. # The Logic Bridge (Key Points)

### The 5 Power Levels
1. **Input/Output:** Single-pass streaming.
2. **Forward:** Multi-pass forward-only.
3. **Bidirectional:** Move both ways (`list`, `map`).
4. **Random Access:** Jump anywhere (`vector`, `deque`).
5. **Contiguous:** Memory is a block (`vector`, `array`).

### Critical Safety: Invalidation
- **Contiguous containers (`vector`)** invalidate everything on resize.
- **Node-based containers (`list`, `map`)** preserve iterators unless the specific node is deleted.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Manual vs Auto)

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

int main() {
    std::vector v = {1, 2, 3, 4, 5};

    // 🚀 Modern Style (Safe)
    auto it = std::find(v.begin(), v.end(), 3);
    if(it != v.end()) std::cout << "Found: " << *it << "\n";

    return 0;
}
```

---

## 🔗 Granular Sub-Topics
- [Iterator Categories](iterator-categories.md) - Power levels and tag dispatching.
- [Iterator Invalidation](iterator-invalidation.md) - When pointers become dangerous.

[➔ Back to STL Hub](00-stl-overview.md)
