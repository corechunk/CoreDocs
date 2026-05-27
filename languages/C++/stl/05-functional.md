# 匿名 STL Lambdas & Functional

## 1. The Objective
Functional programming in C++ allows you to pass "Logic" as an argument to algorithms. Lambdas are anonymous functions defined directly where they are used.

---

## 2. Visual Logic
### The Lambda Anatomy
`[ capture ] ( params ) { body }`
```cpp
// Example: Add 5 to every element
[](int x) { return x + 5; }
```

---

## 3. The Logic Bridge
- **The "Capture" Power:** Unlike standard functions, lambdas can "Capture" variables from the surrounding scope using `[=]` (copy) or `[&]` (reference).
- **Projections (C++20):** Modern algorithms allow you to "project" a data member (like sorting a list of Users by their `age` field) without writing a complex comparator.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Lambda usage)

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

int main() {
    std::vector v = {1, 5, 2, 7, 3};

    // Sort descending using Lambda
    std::sort(v.begin(), v.end(), [](int a, int b) {
        return a > b; 
    });

    std::cout << "Sorted Desc: ";
    for(auto x : v) std::cout << x << " ";

    return 0;
}
```

---
[➔ Back to STL Hub](00-stl-overview.md)
