# 05 - Class Concept (CORE - Hub)

Definition: The `class` is the gateway to Object-Oriented Programming. It combines **Data** (State) and **Methods** (Behavior) into a single entity, enforcing encapsulation by keeping members `private` by default.

## Deep-Dive Reference
For complex hierarchies and pillars:
- [Advanced OOP](./oop/37-advanced-oop.md)

---

## 1. Legacy Way (C++11 / C++17)
Standard class with public methods and private data.

```cpp
#include <iostream>

class Counter {
    int value = 0; // Private by default
public:
    void increment() { value++; }
    int get() const { return value; }
};

int main() {
    Counter c;
    c.increment();
    std::cout << c.get() << "\n"; // Output: 1
    return 0;
}
```

## 2. Modern Way (C++23)
Using **`[[nodiscard]]`** and **`auto`** return types for robust OOP.

```cpp
#include <iostream>

class Counter {
    int value = 0;
public:
    void increment() { value++; }
    [[nodiscard]] auto get() const -> int { return value; }
};

int main() {
    Counter c;
    c.increment();
    std::cout << c.get() << "\n"; // Output: 1
    return 0;
}
```

# The Logic Bridge
// Logic: A class instance (object) is a block of memory on the heap or stack. When a method is called, the compiler implicitly passes the `this` pointer to the function, allowing it to access the instance's private memory layout.
