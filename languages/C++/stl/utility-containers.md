# 📦 STL Pair & Tuple - Master Reference

## 1. The Objective
`std::pair` and `std::tuple` are heterogeneous containers. They allow you to group multiple values of **different types** into a single object. `pair` is limited to two elements, while `tuple` can hold any number.

---

## 2. Visual Logic
### The Multi-Type Box
```text
[ std::pair<string, int> ] -> [ "Alice" | 25 ]
[ std::tuple<int, char, float> ] -> [ 10 | 'Z' | 3.14 ]
```

---

## 3. # The Logic Bridge (Key Points)

- **Return Multiple Values:** The primary use case for `tuple` is allowing a function to return 3+ values without creating a custom `struct`.
- **Lexicographical Comparison:** Both containers support `==` and `<`. They compare elements one by one (first, then second, etc.), which is why they are the default storage for `std::map` keys.
- **Structured Bindings (C++17):** This is the modern way to unpack pairs and tuples. Instead of `p.first`, you use `auto [name, age] = p;`.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Exhaustive Usage)

```cpp
#include <iostream>
#include <utility> // for pair
#include <tuple>
#include <string>

int main() {
    // --- 1. std::pair ---
    std::pair<std::string, double> p = {"Apple", 0.99};
    std::cout << p.first << " costs " << p.second << "\n";

    // --- 2. std::tuple ---
    std::tuple<int, std::string, bool> t = {1, "Active", true};
    
    // Access via std::get<index>
    std::cout << "ID: " << std::get<0>(t) << "\n";

    // --- 3. MODERN UNPACKING (Structured Bindings) ---
    auto [id, status, flag] = t;
    std::cout << "Status: " << status << "\n";

    // --- 4. TIE (Legacy unpacking) ---
    int myId;
    std::tie(myId, std::ignore, std::ignore) = t;

    // --- 5. MAKE HELPERS ---
    auto p2 = std::make_pair(10, "Ten");
    auto t2 = std::make_tuple(1.1, 2.2, 3.3);

    return 0;
}
```

---
[➔ Back to STL Hub](00-stl-overview.md)
