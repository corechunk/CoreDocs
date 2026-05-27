# Abstraction (PRO)

Definition: Hiding implementation details by providing a common interface. Achieved via Pure Virtual Functions.

## 1. Legacy Way (C++11 / C++17)
Abstract classes (Interfaces).

```cpp
class Interface {
public:
    virtual void execute() = 0; // Pure virtual
    virtual ~Interface() = default;
};
```

## 2. Modern Way (C++23)
Using **Concepts** (C++20) for compile-time abstraction and requirements.

```cpp
template<typename T>
concept Executable = requires(T t) {
    t.execute();
};

void run(Executable auto& obj) {
    obj.execute();
}
```

# The Logic Bridge
// Logic: Abstraction focuses on "what" an object does rather than "how." Concepts allow the compiler to verify interfaces at compile-time, providing better error messages than traditional templates.
