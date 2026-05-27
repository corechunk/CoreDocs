# 📈 Dynamic Arrays

## 1. The Objective
A Dynamic Array (like `std::vector` in C++ or `ArrayList` in Java) is a growable array. It solves the fixed-size limitation of static arrays by automatically reallocating more memory when it becomes full.

---

## 2. Visual Logic
### The Growth Cycle
1. **Initial:** `[ A | B | _ | _ ]` (Size: 2, Capacity: 4)
2. **Push C, D:** `[ A | B | C | D ]` (Capacity Full!)
3. **Push E:**
   - Create new array of size **8**.
   - Copy A, B, C, D to new array.
   - Add E.
   - Delete old array.

---

## 3. The Logic Bridge
- **Amortized Efficiency:** While a single push might take $O(n)$ due to resizing, it happens so rarely that the **average (amortized)** cost per push remains **$O(1)$**.
- **Geometric Expansion:** Most dynamic arrays double their size ($2 \times$). This geometric growth is mathematically necessary to achieve $O(1)$ amortized performance.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (std::vector)

```cpp
#include <iostream>
#include <vector>

int main() {
    std::vector<int> v;

    for (int i = 1; i <= 5; i++) {
        v.push_back(i);
        std::cout << "Size: " << v.size() << ", Capacity: " << v.capacity() << "\n";
    }

    return 0;
}
```

---
[➔ Back to Roadmap](../DSA-Master-Roadmap.md)
