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

## 3. The Logic Bridge
- **Iterator Categories:** Not all iterators are equal. 
    - `vector` iterators can jump anywhere ($+5$). 
    - `list` iterators can only move step-by-step (`++`).
- **Modern C++ Advantage:** With `auto` and range-based loops, we rarely write manual iterator code, but understanding them is crucial for using Algorithms like `std::sort`.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Manual vs Auto)

```cpp
#include <iostream>
#include <vector>

int main() {
    std::vector v = {1, 2, 3, 4, 5};

    // 🏛️ Legacy Style
    std::vector<int>::iterator it;
    for(it = v.begin(); it != v.end(); ++it) {
        if(*it == 3) std::cout << "Found 3\n";
    }

    // 🚀 Modern Style
    auto it2 = std::find(v.begin(), v.end(), 4);
    if(it2 != v.end()) std::cout << "Found 4\n";

    return 0;
}
```

---
[➔ Back to STL Hub](00-stl-overview.md)
