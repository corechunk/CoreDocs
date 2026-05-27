# 🧱 Static Arrays & Strings

## 1. The Objective
Static Arrays are the most fundamental data structure. They store elements in **contiguous memory** locations. Strings are essentially specialized arrays of characters. They provide instant access to any element via its index.

---

## 2. Visual Logic
### Contiguity
```text
Index:  [ 0 | 1 | 2 | 3 ]
RAM:    [100|104|108|112] (Assuming 4-byte ints)
Data:   [ A | B | C | D ]
```
- The CPU calculates the address as: `Base + (Index * Size)`. This is why access is $O(1)$.

---

## 3. The Logic Bridge
- **The Tradeoff:** Arrays are "Read-Heavy". You get instant access, but adding or removing elements (except at the end) requires shifting all other items, making it an **$O(n)$** operation.
- **Strings:** In C++, `std::string` is a dynamic array (vector) of chars, but conceptually it follows array logic. Understanding null-termination (`\0`) in C-strings is key to understanding low-level memory handling.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Array vs Vector)

```cpp
#include <iostream>
#include <vector>

int main() {
    // 1. Static Array (Fixed size)
    int arr[5] = {10, 20, 30, 40, 50};
    
    // 2. String Manipulation
    std::string s = "CoreChunk";
    s[0] = 'c'; // O(1) access

    std::cout << "Array Element 2: " << arr[2] << std::endl;
    std::cout << "Modified String: " << s << std::endl;

    return 0;
}
```

---
[➔ Back to Roadmap](../DSA-Master-Roadmap.md)
