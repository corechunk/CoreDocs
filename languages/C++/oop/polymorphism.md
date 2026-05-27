# Polymorphism (PRO)

Definition: Allowing a single interface to represent different underlying forms (data types). In C++, this is mostly achieved via virtual functions.

## 1. Legacy Way (C++11 / C++17)
Pointer-based polymorphism.

```cpp
#include <iostream>

class Base {
public:
    virtual void speak() { std::cout << "Base\n"; }
};

class Derived : public Base {
public:
    void speak() override { std::cout << "Derived\n"; }
};
```

## 2. Modern Way (C++23)
Using **`std::variant`** and **`std::visit`** for compile-time polymorphism (Type-safe union).

```cpp
#include <variant>
#include <iostream>

struct Cat { void speak() const { std::cout << "Meow\n"; } };
struct Dog { void speak() const { std::cout << "Woof\n"; } };

using Animal = std::variant<Cat, Dog>;

int main() {
    Animal a = Cat{};
    std::visit([](auto&& arg) { arg.speak(); }, a); // Output: Meow
    return 0;
}
```

# The Logic Bridge
// Logic: While virtual functions use runtime dynamic dispatch (vtable), `std::variant` uses compile-time dispatch, which can be significantly faster by avoiding pointer indirection.
