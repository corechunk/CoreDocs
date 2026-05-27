# 匿名 STL Lambdas (Anonymous Functions)

## 1. The Objective
Lambdas are one of the most powerful features of Modern C++ (C++11 and later). They allow you to define a function object directly in the middle of your code, making algorithms like `std::sort` or `std::find_if` much more readable and concise.

---

## 2. Visual Logic
### The Anatomy
```text
[ capture ] ( parameters ) mutable -> return_type { body }
```
- **Capture:** Access to variables in the surrounding scope.
- **Mutable:** Allows modifying captured-by-value variables.

---

## 3. The Logic Bridge
- **The "Function Object" Reality:** A lambda is not just a function pointer; it's a compiler-generated **Class** with an `operator()`. The "captures" are stored as member variables of this class.
- **Capturing Strategies:**
    - `[=]` : Capture all variables by Value (Copy).
    - `[&]` : Capture all variables by Reference.
    - `[x, &y]` : Capture `x` by value and `y` by reference.
- **Performance:** Because the compiler knows the exact logic of the lambda at compile-time, it can often inline the code, making it **faster** than using a traditional function pointer.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Full Usage)

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

int main() {
    int factor = 10;
    std::vector v = {1, 2, 3};

    // 1. Capture by Value
    std::for_each(v.begin(), v.end(), [factor](int n) {
        std::cout << n * factor << " ";
    });

    // 2. Capture by Reference (Modifying local state)
    int sum = 0;
    std::for_each(v.begin(), v.end(), [&sum](int n) {
        sum += n;
    });

    // 3. Generic Lambda (C++14)
    auto print = [](auto x) { std::cout << x << " "; };
    print(100);
    print("Hello");

    return 0;
}
```

---
[➔ Back to Functional Hub](05-functional.md)
