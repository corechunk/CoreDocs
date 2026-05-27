# Interfaces (PRO)

Definition: A contract that defines a set of methods a class must implement. In C++, interfaces are implemented using abstract classes with only pure virtual functions.

## 1. Legacy Way (C++11 / C++17)
Standard abstract interface.

```cpp
class IDrawable {
public:
    virtual void draw() const = 0;
    virtual ~IDrawable() = default;
};
```

## 2. Modern Way (C++23)
Using **Concepts** as a modern interface alternative.

```cpp
template<typename T>
concept Drawable = requires(T t) {
    t.draw();
};
```

# The Logic Bridge
// Logic: C++ does not have a dedicated `interface` keyword. Pure virtual functions create an "interface" at the object level (vtable), while Concepts create an "interface" at the type level during compilation.
