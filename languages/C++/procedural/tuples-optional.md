# Tuples & Optional (PRO)

Definition: Procedural data containers for returning multiple values or handling nullable states without complex class hierarchies.

## 1. Legacy Way (C++11 / C++17)
Using `std::pair` and manual error codes.

```cpp
#include <utility>
std::pair<int, int> get_range() { return {0, 10}; }
```

## 2. Modern Way (C++23)
Using **`std::tuple`**, **Structured Bindings**, and **`std::optional`**.

```cpp
#include <tuple>
#include <optional>

auto get_user() -> std::tuple<int, const char*> { return {1, "Core"}; }

int main() {
    auto [id, name] = get_user(); // Structured binding
    std::optional<int> data = 42;
    if (data) { /* use *data */ }
}
```

# The Logic Bridge
// Logic: `std::optional` provides a type-safe way to represent a value that may or may not exist, replacing the dangerous C-pattern of returning NULL pointers or magic error numbers like -1.
