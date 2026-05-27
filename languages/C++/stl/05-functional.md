# 匿名 STL Functional & Lambdas

## 1. The Objective
Functional programming in C++ allows you to pass "Logic" as an argument to algorithms. This decoupling of "What to do" from "How to iterate" is the core strength of the STL.

---

## 2. Visual Logic
### The Callable Hierarchy
- **Functions:** Global/Static logic.
- **Functors:** Classes with `operator()`.
- **Lambdas:** Inline, anonymous functors.
- **`std::function`:** A container that can hold any of the above.

---

## 3. # The Logic Bridge (Key Points)

### Lambda Captures
- `[]` : No capture.
- `[=]` : Capture all by **Value**.
- `[&]` : Capture all by **Reference**.
- `[this]` : Capture current class instance.

### When to use `std::function`?
Use when you need to **store** logic for later use (e.g., event listeners, command patterns) where the exact type of the callable is unknown at compile-time. Avoid in high-frequency loops where templates or raw lambdas are faster.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Abstract Example)

```cpp
#include <iostream>
#include <functional>

int main() {
    // A simple lambda
    auto greet = []() { std::cout << "Hello Functional C++!" << std::endl; };
    greet();

    return 0;
}
```

---

## 🔗 Granular Sub-Topics
- [Lambdas In-Depth](lambdas.md) - Capture groups and mutable logic.
- [std::function](std-function.md) - Type erasure and polymorphic callables.

[➔ Back to STL Hub](00-stl-overview.md)
