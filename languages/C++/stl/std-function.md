# 📦 std::function (Polymorphic Wrapper)

## 1. The Objective
`std::function` is a general-purpose polymorphic function wrapper. It can store, copy, and invoke any **Callable** target—functions, lambdas, bind expressions, or other function objects—as long as they match the specified signature.

---

## 2. Visual Logic
### The "Logic Box"
```text
[ std::function<void(int)> ]
          |
    ------------------
    |                |
 [ Lambda ]   [ Regular Func ]
```
- One variable can hold different types of callables.

---

## 3. The Logic Bridge
- **Type Erasure:** This is the core magic. `std::function` "erases" the specific type of the callable and only cares about the **Signature** (Input/Output types).
- **Flexibility vs. Performance:** Because it uses dynamic memory (heap) and virtual function calls internally, `std::function` is slightly slower than a raw lambda or template. Use it when you need to store logic (like a list of "Callbacks") but not in tight performance loops.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Full Usage)

```cpp
#include <iostream>
#include <functional>
#include <vector>

void regularFunc(int x) { std::cout << "Func: " << x << "\n"; }

int main() {
    // Wrapper for any function that takes (int) and returns (void)
    std::function<void(int)> f;

    // 1. Store regular function
    f = regularFunc;
    f(10);

    // 2. Store lambda
    f = [](int x) { std::cout << "Lambda: " << x << "\n"; };
    f(20);

    // 3. Storing a list of actions
    std::vector<std::function<void(int)>> callbacks;
    callbacks.push_back(regularFunc);
    callbacks.push_back(f);

    for (auto& cb : callbacks) cb(100);

    return 0;
}
```

---
[➔ Back to Functional Hub](05-functional.md)
