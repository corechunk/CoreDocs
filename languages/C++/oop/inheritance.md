# Inheritance (PRO)

Definition: A mechanism where a class (derived) can inherit properties and behaviors from another class (base).

## 1. Legacy Way (C++11 / C++17)
Basic inheritance and access specifiers.

```cpp
class Base {
protected:
    int id;
};

class Derived : public Base {
public:
    void setId(int n) { id = n; }
};
```

## 2. Modern Way (C++23)
Using **`final`** and **`override`** to prevent errors and ensure correct overrides.

```cpp
class Base {
public:
    virtual void run() = 0;
};

class Derived final : public Base {
public:
    void run() override { /* impl */ }
};
```

# The Logic Bridge
// Logic: Inheritance creates an "is-a" relationship. The derived class object contains a sub-object of the base class type in its memory layout.
