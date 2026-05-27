# Encapsulation (PRO)

Definition: Restricting direct access to data and providing controlled access through methods. In C++, this is achieved via access specifiers (`public`, `private`, `protected`).

## 1. Legacy Way (C++11 / C++17)
Standard access specifiers and manual getters/setters.

```cpp
#include <string>

class User {
private:
    std::string name;
public:
    void setName(const std::string& n) { name = n; }
    std::string getName() const { return name; }
};
```

## 2. Modern Way (C++23)
Using **`[[nodiscard]]`**, **`const`** correctness, and `auto` for cleaner encapsulation.

```cpp
#include <string>

class User {
private:
    std::string name;
public:
    // nodiscard ensures the return value isn't ignored
    [[nodiscard]] auto get_name() const -> const std::string& { 
        return name; 
    }
};
```

# The Logic Bridge
// Logic: Encapsulation ensures that the internal state of an object can only be changed in ways defined by the programmer, preventing external code from corrupting data.
